+++
languageCode = "bn-bd"
title = "A Complete Overview of vim for Scared Beginner"
author = "Nuhil Mehdy"
categories = ["Tools"]
tags = ["vim", "vim plug", "nerdtree", "text editor"]
date = 2017-11-11T00:00:00-00:00
description = "A breif walkthrough to vim introduction, basic configuration, plugin management with vim plug, linting, color scheme and more."
featured = ""
featuredalt = "vim"
featuredpath = ""
linktitle = ""
type = "post"

draft = true
+++

## Introduction
---
vim is simply a text editor. To be more specific, its a Terminal based text editor. Its a charityware, means its free to use but you can donate which will be spent for the poor childrens of Uganda. Few facts about vim -   

* Actual name of this tool is `vi` and `vim` means `vi` `im`proved :)
* Comes with almost every Unix based system as `vi`
* Persistent, multi-level undo tree
* Extensive plugin system
* Support for hundreds of programming languages and file formats
* Powerful search and replace
* Integrates with many tools

## Installation & Usage
---
If you got any Unix based system like Ubuntu, Debian, Mint, CentOS, macOS etc. then you should have vim installed already in that OS/distribution. So, just check whether it is ready to use by issuing the following command in your Terminal - 

```sh
vim
```

If it shows an intro screen that is similar to below, then everything is fine. To get out from that editor intro screen, just type `:q` in your keyboard and press enter.   

*Watch the below terminal cast* 

<center>
<script type="text/javascript" src="https://asciinema.org/a/149392.js" id="asciicast-149392" async></script>
</center>

But if you have a simpler version of Linux then you could install it using respective package repository. For example, in Ubuntu, it could be done by the following command - 

```sh
sudo apt-get install vim
```

**Start Writing a File**   
Lets create an example project directory in our home folder named `app` (assume we are going to create a Node.js app) and enter inside it by `cd app`. Then from inside the directory, issue the following command to start writing a file named `index.js` - 

```sh
vi index.js
```

You will get a blank screen which is basically the file to be written (`index.js` in this case). Now, to start writing in this file you have to first enable the insert mode of the running vim editor. For this, just press `i` in your keyboard and you will see `INSERT` on the bottom left part of the Terminal which indicates that you just entered into insert mode of the editor. From now on, type anything in your keyboard and those keystrokes are going to be written in the opened file.  

After writing something in the file, you would like to save the content, right? Just like we do in visual editors by pressing Control+s or Command+s for saving our work so far. To do this in vim, you first have to come back in vim's visual mode. Till now we are in insert mode (remember?).   

To get back into visual mode, just press the `Esc` button in your keyboard. Now, you can pass command to vim editor rather than writing in the file. Being in the visual mode, type `:w` in your keyboard and those two characters will be shown on the bottom left part of your terminal which indicates that you are about to give some command to vim. Just press Enter after typing `:w` and the command will be sent to vim which will tell vim to save this state of this file to the memory.   

So, its very logical that you are still seeing the file opened in which you are writing, right? Its because you have not closed the file yet. To close the file just pass the command `:q` to vim. You remember how to pass command to vim? Let me tell again - make sure you are not in insert mode by pressing `Esc` in your keyboard and then type `:q` and press `Enter`. The file as well as the vim editor will be closed.  

So far we have successfully wrote a file named `index.js` and saved it in the file system. To verify that, you can issue list command in your terminal and you should see, there is a file inside the `app` folder - 

*Watch the below terminal cast* 

<center>
<script type="text/javascript" src="https://asciinema.org/a/149393.js" id="asciicast-149393" async></script>
</center>