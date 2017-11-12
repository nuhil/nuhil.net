+++
languageCode = "bn-bd"
title = "Virtual Environment for Python Workspace Part 3/3 venv"
author = "Nuhil Mehdy"
categories = ["Python"]
tags = ["python", "virtual environment", "virtualenv", "conda", "venv"]
date = "2017-10-03"
description = "How to create virtual environment in Python using venv."
featured = ""
featuredalt = ""
featuredpath = "date"
linktitle = ""
type = "post"
+++

In the earlier two posts of this series, I discussed about `virtualenv`  and `conda`  and their usage along with some examples. I this post I am going to introduce you guys with another package and environment manager called `venv`  which comes with standard Python3.X by default. So, nothing to worry about its installation.

[Virtual Environment for Python Workspace – Part 1/3 – virtualenv](http://localhost:1313/blog/virtual-environment-for-python-workspace-part-1-3-virtualenv/)  
[Virtual Environment for Python Workspace – Part 2/3 – conda](/blog/virtual-environment-for-python-workspace-part-2-3-conda/)

## Creating an Environment
For example, If you have Python3.X installed in your system and you can run it's REPL by issuing `python3` in the terminal, then you can create a virtual environment based on this Python version by issuing the following command:
```sh
python3 -m venv myvenv
```
This will create the `myvenv`  directory if it doesn’t exist, and also create directories inside it containing a copy of the Python interpreter, the standard library, and various supporting files. By the way, you got the idea of using different versions of Python to use its `venv`  module for creating different environments, right? Just find out an exact Python 3.X (I showed how, in earlier posts) and use its binary/executable in the command `<active python> -m venv <environment name>` .

## Activating the Environment
Its similar to the previous two workarounds and again simple as below. I assumed you are inside the newly created `myvenv`  directory.
```sh
source bin/activate
```
## Managing Packages with pip
As `venv`  is native with Python, you can use `pip`  for installing packages in your virtual environment which will pull down packages from Python's official package repository, PyPI. For example, to install our very favorite package `numpy` , use the following command,
```sh
pip install numpy
```
Also, for sure you can use commands like `pip search <packagename>` ,`pip list` in each newly created virtual environment.

> Did you know, you can use `pip show <packagename>`  to see detail of an installed package in an active environment?

## Sharing Environment
In the earlier post, I have discussed why and how you can share your environment made using `conda`  with others. If you are using `venv`  or `virtualenv`  then you can export an environment's state/configuration to a file, issuing the following command,
```sh
pip freeze > requirements.txt
```
Here, the file name `requirements.txt` , that contains environment's package information could be anything. But people have been using this name conventionally for a long time.

So, after exporting the environment information, you can share this file to any one who can install exact same packages in his newly created virtual environment by using the following command:
```sh
pip install -r requirements.txt
```

> By the way, sharing environment in this way is similar if you use `virtualenv`

## Resources

* https://docs.python.org/3/tutorial/venv.html

> **Do you love Watching than Reading?**  
[Subscribe](https://www.youtube.com/channel/UCJFY9iVRXTJu1SPVI_vRNDw) & Get Connected with my [YouTube](https://www.youtube.com/channel/UCJFY9iVRXTJu1SPVI_vRNDw) channel for Video version of all my Blog posts.