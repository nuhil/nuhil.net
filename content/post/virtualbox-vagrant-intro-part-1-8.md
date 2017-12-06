+++
languageCode = "bn-bd"
title = "Virtualbox + Vagrant - Introduction. Part 1/8"
author = "Nuhil Mehdy"

categories = ["Tools", "Dev Ops"]
tags = ["virtualbox", "vagrant"]

date = 2017-12-06T00:00:00-00:00

description = ""
featured = ""
featuredalt = "vagrant"
featuredpath = ""
linktitle = ""
type = "post"

draft = true
+++

### Introduction and Installation
---
VirtualBox, since it is free, available on every major platform, and built-in to Vagrant. Vagrant can work with many other providers.

Some operating system distributions include a vagrant package in their upstream package repos. Please do not install Vagrant in this manner.

Verify installation - 
```sh
vagrant
```
<!--more-->

## Project Setup
--- 

Vagrant has a built-in command for initializing a directory for usage with Vagrant.

```sh
$ mkdir myvm
$ cd myvm
$ vagrant init
```

This will place a Vagrantfile in your current directory. You can take a look at the Vagrantfile if you want. The Vagrantfile is meant to be committed to version control with your project, if you use version control.


Instead of building a virtual machine from scratch, which would be a slow and tedious process, Vagrant uses a base image to quickly clone a virtual machine. These base images are known as "boxes" in Vagrant.

Boxes are added to Vagrant with vagrant box add.

```sh
$ vagrant box add ubuntu/trusty64
```

You can also add boxes from a local file, custom URL, etc. Boxes are globally stored for the current user. Each project uses a box as an initial image to clone from, and never modifies the actual base image.

Open the Vagrantfile and change the contents to the following:

```sh
Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/trusty64"
end
```

If the box was not added before, Vagrant will automatically download and add the box when it is run. You may specify an explicit version of a box by specifying config.vm.box_version for example - 

```sh
Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/trusty64"
  config.vm.box_version = "20171115.1.2"
end
```

More boxes - https://app.vagrantup.com/boxes/search
HashiCorp's Vagrant Cloud lets you host your own boxes, as well as private boxes if you intend on creating boxes for your own organization.

### Up & Running
---
```sh
$ vagrant up
```
You can SSH into the machine - 

```sh
$ vagrant ssh
```

Be careful about rm -rf /, since Vagrant shares a directory at /vagrant with the directory on the host containing your Vagrantfile, and this can delete all those files.

The SSH session can be terminated with CTRL+D

```sh
vagrant@precise64:~$ logout
```

```sh
vagrant destroy
```

The `vagrant destroy` command does not actually remove the downloaded box file. To completely remove the box file, you can use the `vagrant box remove` command.

## Folder Synchronisation
---

Not many people want to edit files using just plain terminal-based editors over SSH. y using synced folders, Vagrant will automatically sync your files to and from the guest machine.

By default, Vagrant shares your project directory (remember, that is the one with the Vagrantfile) to the /vagrant directory in your guest machine.

Note that when you vagrant ssh into your machine, you're in /home/vagrant. /home/vagrant is a different directory from the synced /vagrant directory.

Up Again - 

```sh
$ vagrant up
$ vagrant ssh
vagrant@precise64:~$ ls /vagrant
```

That Vagrantfile you see inside the virtual machine is actually the same Vagrantfile that is on your actual host machine.

```sh
vagrant@precise64:~$ touch /vagrant/foo
vagrant@precise64:~$ exit
$ ls
foo Vagrantfile
```

Point to custom folder -

```sh
config.vm.synced_folder "~/Documents/LAMP", "/var/www/html"
```

## Provisioning
---

Alright, so we have a virtual machine running a basic copy of Ubuntu and we can edit files from our machine and have them synced into the virtual machine. Let us now serve those files using a webserver.

We could just SSH in and install a webserver and be on our way, but then every person who used Vagrant would have to do the same thing. Instead, Vagrant has built-in support for automated provisioning. Using this feature, Vagrant will automatically install software when you vagrant up so that the guest machine can be repeatably created and ready-to-use.

We will just setup Apache for our basic project, and we will do so using a shell script. Create the following shell script and save it as `bootstrap.sh` in the same directory as your Vagrantfile:

```sh
#!/usr/bin/env bash

apt-get update
apt-get install -y apache2
if ! [ -L /var/www ]; then
  rm -rf /var/www
  ln -fs /vagrant /var/www
fi
```

Next, we configure Vagrant to run this shell script when setting up our machine. We do this by editing the Vagrantfile - 

```sh
Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/trusty64"
  config.vm.provision :shell, path: "bootstrap.sh"
end
```

The "provision" line is new, and tells Vagrant to use the shell provisioner to setup the machine, with the bootstrap.sh file. 

After everything is configured, just run `vagrant up` to create your machine and Vagrant will automatically provision it. 

If the guest machine is already running from a previous step, run `vagrant reload --provision`

After Vagrant completes running, the web server will be up and running. You cannot see the website from your own browser (yet), but you can verify that the provisioning works by loading a file from SSH within the machine:

```sh
$ vagrant ssh
...
vagrant@precise64:~$ wget -qO- 127.0.0.1
```

It may be more efficient to package a custom Vagrant box with those packages pre-installed instead of building them each time.

 ## Networking & Sharing
---
In this step, we will use Vagrant's networking features to give us additional options for accessing the machine from our host machine.

**Port Forwarding**   
This allows you to access a port on your own machine, but actually have all the network traffic forwarded to a specific port on the guest machine. Let us setup a forwarded port so we can access Apache in our guest.

```sh
Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/trusty64"
  config.vm.provision :shell, path: "bootstrap.sh"
  config.vm.network :forwarded_port, guest: 80, host: 4567
end
```
Run a `vagrant reload`

Once the machine is running again, load http://127.0.0.1:4567

**Private Network**  

```sh
config.vm.network "private_network", ip: "192.168.33.10"
```

**Sharing**   
Vagrant Share lets you share your Vagrant environment to anyone around the world with an Internet connection.

```sh
$ vagrant share
```

To end the sharing session, hit Ctrl+C in your terminal

## Teardown & Rebuild
---
Suspending the virtual machine by calling vagrant suspend will save the current running state of the machine and stop it.

Halting the virtual machine by calling vagrant halt will gracefully shut down the guest operating system and power down the guest machine. You can use vagrant up when you are ready to boot it again.

Destroying the virtual machine by calling vagrant destroy will remove all traces of the guest machine from your system. It'll stop the guest machine, power it down, and remove all of the guest hard disks. 

When you are ready to come back to your project, whether it is tomorrow, a week from now, or a year from now, getting it up and running is easy:

```sh
vagrant up
```

**Providers**   
But Vagrant can work with a wide variety of backend providers, such as VMware, AWS, and more.
Once you have a provider installed, you do not need to make any modifications to your Vagrantfile, just vagrant up with the proper provider and Vagrant will do the rest:

```sh
vagrant up --provider=vmware_fusion
```
