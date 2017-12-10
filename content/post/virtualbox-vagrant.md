+++
languageCode = "bn-bd"
title = "[Video] Virtualbox with Vagrant - Complete Overview for Beginners"
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
+++

---
In this YouTube playlist I have covered all the basic steps needed for getting started with Vagrant along with VirtualBox. I have demonstrated the following topics in these screencasts - 

* Introduction and Installation
* Project Setup
* Up & Running
* Folder Synchronisation
* Provisioning
* Networking & Sharing
* Teardown & Rebuild

<!--more-->
<center>
<iframe width="560" height="315" src="https://www.youtube.com/embed/G2dUnr9frLs" frameborder="0" gesture="media" allow="encrypted-media" allowfullscreen></iframe>
</center>

In the first video I went through the introduction of both VirtualBox and Vagrant and some of their Pros and Cons. Later in the second video, I have demonstrated the installation process of these two Softwares.   

Later, I have shown how an example project can be created to demonstrate all the topics on. Then, the next screencast shows how a virtual environment can be boot up for further usage.   

In the *Folder Synchronisation* part, I have demonstrated about files and data synchronisation between the Host machine and Guest (virtual) machine so that it become easier to manipulate files from inside the Host machine using native tools.

Then, the most important topic *Provisioning* was covered where I have described the simpler way of provisioning a virtual machine based on Shell script and using Vagrant's shell provisioner facility.    

While dealing with single or multiple virtual machines in a Host environment, its very usual to have the proper knowledge of networking among those isntances. I also covered this step where viewer will understand about private networking and also about exposing local environment to the Internet.

Finally, I have shown how the virtual environments can be destroyed fully and rebuild on purpose quickly. Also, I have demonstrated how the whole infrastructure can be shared with collaborators and they can boot up a similar environment by just a single command.

