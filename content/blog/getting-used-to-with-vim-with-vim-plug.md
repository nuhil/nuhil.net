+++
languageCode = "bn-bd"
title = "A Complete Overview of vim for Scared Beginner"
author = "Nuhil Mehdy"
categories = ["Tools"]
tags = ["vim", "vim plug", "nerdtree", "text editor"]
date = "2017-11-11"
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

* actual name of this tool is `vi` and `vim` means `vi` `im`proved :)
* comes with almost every Unix based system as `vi`
* persistent, multi-level undo tree
* extensive plugin system
* support for hundreds of programming languages and file formats
* powerful search and replace
* integrates with many tools

## Installation & Usage
---
If you got any Unix based system like Ubuntu, Debian, Mint, CentOS, macOS etc. then you should have vim installed already in that OS/distribution. So, just check whether it is ready to use by issuing the following command in your Terminal - 

```sh
vim
```

If it shows an intro screen that is similar to below, then everything is fine and to get out from that editor intro screen, just type `:q` in your keyboard and press enter. *(watch below for demo)* 

<script type="text/javascript" src="https://asciinema.org/a/148230.js" id="asciicast-148230" async></script>

But if you have a simpler version of Linux then you could install it using respective package repository. For example, in Ubuntu, it could be done by the following command - 

```sh
sudo apt-get install vim
```
