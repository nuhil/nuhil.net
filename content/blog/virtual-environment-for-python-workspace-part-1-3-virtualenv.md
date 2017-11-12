+++
languageCode = "bn-bd"
title = "Virtual Environment for Python Workspace Part 1/3 Virtualenv"
author = "Nuhil Mehdy"
categories = ["Python"]
tags = ["python", "virtual environment", "virtualenv"]
date = "2017-10-01"
description = "How to create virtual environment in Python using virtualenv."
featured = ""
featuredalt = ""
featuredpath = "date"
linktitle = ""
type = "post"
+++

If you are planning to work or have been working in Python stack for web development, machine learning, data analysis etc. then you must have already come through the term "virtual environment". In this article I will try to explain what it is, why its needed and how to acheive this workaround in three different ways. I will give you a basic overview of creating and managing Python virtual environment with `virtualenv` , `venv`  and `conda`  (with miniconda). So, lets start.

## What is Python virtual environment and why it's needed?
Suppose, you have only one computer for development or even a single VPS for deployment. Obviously you will not develop a single application in your whole life, right? As a software developer you will have to develop bunch of tools, modules, softwares, scripts in your entire lifecycle. Let's not go that much deeper for now :P

Assume that, you are developing an application which needs version 1.0 of a certain library/package and so far its working nice based on its dependency(s). Here by dependency, I mean that specific library/package. What if, you start developing another app or got responsibility to contribute in an ongoing application and fortunately you found that, this app also uses that exact same library/package you already have installed in your system; and unfortunately you also found that it works only for a different version of that so called library? So, its quite normal that, an application can depend on different packages of different versions and there is nothing wrong with this situation. Even, different app can depend of different versions of Python (interpreter), seems fair, right?

Here comes the necessity of app specific dependency management. This dependency is not only on library or packages but also could on Python versions. Another important issue arises while developing in Python stack is, the chance of messing up your system's native Python installation. Every *Nix like operating system comes with Python pre-installed. You already know that :) Even, recent distributions are coming with two or more versions of Python pre-installed (You can access those different REPL by issuing commands like `python`  or `python3`  in the terminal).

But why so? Because, it could be happened that, some OS specific tools or programs use Python 2.X for their own needs. On the other hand users can expect to have an updated version of Python in that system for their custom development. Now, if you install all your required libraries and packages in global package (in `site-packages`  directory if specifically said) scope, then very soon it will be a mess up. What you could do is to install needed packages to the location where Python 3.X resides. Still that above mentioned situation could be raised where you may need different versions of libraries for different developing apps.

So, need for having isolated Python environments is so casual. If we can make different Python environments; based on different versions of Python and install very specific libraries and packages in it, then everything will be more organized and loosely coupled with the native system. `virtualenv`  is such a package that helps you to make unlimited number of virtual environments and configure them according to your various needs. It creates an environment that has its own installation directories, that doesn’t even share libraries with other `virtualenv`  environments (and optionally doesn’t access the globally installed libraries either).

## Installing virtualenv
To install globally with pip (if you have pip 1.3 or greater installed globally), issue the following command in your terminal:
```sh
pip install virtualenv
```
## Creating New Virtual Environment(s)
To create a virtual enviornment named `myenvironment`  for example, issue the following command in the terminal:
```sh
virtualenv myenvironment
```
As soon as the above environment is created, several directories and files are also created inside the `myenvironment`  folder. You will see directory like `myenvironment/bin` where the python interpreter or executeable for this specific environment is placed. Directories like `myenvironment/lib` & `myenvironment/include`  contains supporting libraries for this python environment. Thus, for obvious reason - packages that will be installed in this new environment will live under `myenvironment/lib/pythonX.X/site-packages/` directory. Its worth mentioning that, with each new virtual environment creation, it automatically installs the `pip` , `wheel`  & `setuptools`  package.

## Activating a Virtual Environment
If you are inside the environment directory which means inside the `myenvironment`  folder as per this example, then issuing the following command will activate the virtual environment:
```sh
source bin/activate
```
The activate script will also modify your shell prompt to indicate which environment is currently active. If you see the following terminal activity then you will understand what I am talking about.
```sh
Nuhils-MacBook-Pro:~ nuhil$ virtualenv myenvironment
New python executable in /Users/nuhil/myenvironment/bin/python
Installing setuptools, pip, wheel...done.

Nuhils-MacBook-Pro:~ nuhil$ cd myenvironment/
Nuhils-MacBook-Pro:myenvironment nuhil$ source bin/activate

(myenvironment) Nuhils-MacBook-Pro:myenvironment nuhil$
```
In the above logs, first I created the virtual environment. Then while creating the environment, `pip` , `wheel` , & `setuptools`  are also being installed in the new environment. After that, I issued command to activate the environment and it prepended the environment name infront of the command prompt which indicates that the shell has been updated to use the new python environment from now on.

As this environment is now active, why not check what packages are installed and ready to use in this brand new fresh python environment? For that, issue the following command:
```sh
pip list
```
Which will output something like below,
```sh
(myenvironment) Nuhils-MacBook-Pro:myenvironment nuhil$ pip list
pip (9.0.1)
setuptools (36.5.0)
wheel (0.30.0)
```
Which clearly shows that we have only three packages installed in this new environment. By the way, would you like to check which `pip`  it is? I mean is this `pip`  belong to this environment or its something else? Check that by:
```sh
which pip
```
and you will see something like following,
```sh
(myenvironment) Nuhils-MacBook-Pro:myenvironment nuhil$ which pip
/Users/nuhil/myenvironment/bin/pip
```
that clearly shows that, its belong to the newly created virtual environment. Even you can check whats the responsible Python here in this environment by the following command:
```sh
which python
```
and you will see output similar to below,
```sh
(myenvironment) Nuhils-MacBook-Pro:myenvironment nuhil$ which python
/Users/nuhil/myenvironment/bin/python
```
which indicates that the python in this context is also belongs to the virtual environment. You are already feeling isolation, right? :) So, lets install few packages here inside the virtual environment using it's pip.
```sh
(myenvironment) Nuhils-MacBook-Pro:myenvironment nuhil$ pip install numpy
Collecting numpy
  Downloading numpy-1.13.3-cp27-cp27m-macosx_10_6_intel.macosx_10_9_intel.macosx_10_9_x86_64.macosx_10_10_intel.macosx_10_10_x86_64.whl (4.6MB)
    100% |████████████████████████████████| 4.6MB 176kB/s 
Installing collected packages: numpy
Successfully installed numpy-1.13.3
```
Again, lets check package list of this new environment:
```sh
(myenvironment) Nuhils-MacBook-Pro:myenvironment nuhil$ pip list
numpy (1.13.3)
pip (9.0.1)
setuptools (36.5.0)
wheel (0.30.0)
```
Impressed? We are installing only our needed packages in this new virtual environment without messing around the native python environment or global package scope.

## Using the Environment
Just after activating the environment, its ready to use. For example, lets create a Python script like following:
```python
import numpy as np
a = np.array([2,3,4])
print(a)
```
Keep in mind that, you are not bound to create Python scripts/apps inside the environment. You are free to create those files anywhere in your system. You just make use of a virtual environment by activating it and run any Python scripts/apps through it's python executable. Check the following terminal activity:
```sh
(myenvironment) Nuhils-MacBook-Pro:~ nuhil$ cd ~/Desktop/
(myenvironment) Nuhils-MacBook-Pro:Desktop nuhil$ vi test.py
(myenvironment) Nuhils-MacBook-Pro:Desktop nuhil$ python test.py
[2 3 4]
```
Here I have moved to Desktop, created a file called `test.py`  and put the above code in it. Finally run it with python interpreter and got expected output. Keep in mind, my virtual environment is still in active mode.

## Deactivating the Environment
It's as easy as issuing the following command:
```sh
(myenvironment) Nuhils-MacBook-Pro:Desktop nuhil$ deactivate
Nuhils-MacBook-Pro:Desktop nuhil$
```
Did you notice, how the prepended environment just gone? It means you are now back not the normal shell.

## Creating Environment based on Different Python Versions
So far have you ever think when we are creating a virtual environment, we are not downloading Python from anywhere? Still we are getting python executable inside the virtual environment. How does it happen? Well, it's actually making a symbolic link of the `Python`  to which this `virtualenv`  package belongs to. Lets check this out - enter into the virtual environment folder and look into all the files including hidden ones by issuing the command:
```sh
Nuhils-MacBook-Pro:~ nuhil$ cd myenvironment/

Nuhils-MacBook-Pro:myenvironment nuhil$ ls -al
total 16
drwxr-xr-x   7 nuhil  staff   238 Oct  5 03:50 .
drwxr-xr-x+ 53 nuhil  staff  1802 Oct  5 04:31 ..
lrwxr-xr-x   1 nuhil  staff    63 Oct  5 03:50 .Python -> /System/Library/Frameworks/Python.framework/Versions/2.7/Python
drwxr-xr-x  17 nuhil  staff   578 Oct  5 04:05 bin
drwxr-xr-x   3 nuhil  staff   102 Oct  5 03:50 include
drwxr-xr-x   3 nuhil  staff   102 Oct  5 03:50 lib
-rw-r--r--   1 nuhil  staff    60 Oct  5 03:50 pip-selfcheck.json
```
I hope, you can see a link to my system's default Python which is located in `/System/Library/Frameworks/Python.framework/Versions/2.7/Python` . But, just like you, I don't also want to use that old Python for my fresh new virtual environment, rather I want to use Python 3 with some fresh packages that I need for a project.

Fortunately its possible. Say, you have downloaded Python 3.X from the official website and installed it in your computer. Its also possible that, you downloaed anaconda or miniconda and that also installed another version of Python in your computer. But so far, you have come to know that, you just need the Python executable and you are free to make isolated environments. But, may be you don't know where all the different Python versions actually reside. Let's find those.
```sh
Nuhils-MacBook-Pro:~ nuhil$ ls /usr/bin/ | grep python
python
python-config
python2.6
python2.6-config
python2.7
python2.7-config
pythonw
pythonw2.6
pythonw2.7
```
Yeah, I found some 2.X versions of Python. Lets try to find more:
```sh
Nuhils-MacBook-Pro:~ nuhil$ ls -al /usr/local/bin/ | grep python
lrwxr-xr-x    1 root   wheel        69 Mar 10  2017 python3 -> ../../../Library/Frameworks/Python.framework/Versions/3.6/bin/python3
lrwxr-xr-x    1 root   wheel        72 Mar 10  2017 python3-32 -> ../../../Library/Frameworks/Python.framework/Versions/3.6/bin/python3-32
lrwxr-xr-x    1 root   wheel        76 Mar 10  2017 python3-config -> ../../../Library/Frameworks/Python.framework/Versions/3.6/bin/python3-config
lrwxr-xr-x    1 root   wheel        71 Mar 10  2017 python3.6 -> ../../../Library/Frameworks/Python.framework/Versions/3.6/bin/python3.6
lrwxr-xr-x    1 root   wheel        74 Mar 10  2017 python3.6-32 -> ../../../Library/Frameworks/Python.framework/Versions/3.6/bin/python3.6-32
lrwxr-xr-x    1 root   wheel        78 Mar 10  2017 python3.6-config -> ../../../Library/Frameworks/Python.framework/Versions/3.6/bin/python3.6-config
lrwxr-xr-x    1 root   wheel        72 Mar 10  2017 python3.6m -> ../../../Library/Frameworks/Python.framework/Versions/3.6/bin/python3.6m
lrwxr-xr-x    1 root   wheel        79 Mar 10  2017 python3.6m-config -> ../../../Library/Frameworks/Python.framework/Versions/3.6/bin/python3.6m-config
```
Lets say, we want to make a new virtual environment based on Python 3.6 & from the above search, we know that our system has that installed already (or may be I once installed and forgot). So, issuing the following command will make a brand new Python virtual environment that will be based on Python 3.6:
```sh
Nuhils-MacBook-Pro:~ nuhil$ virtualenv -p /usr/local/bin/python3.6 mynewenvironment
Running virtualenv with interpreter /usr/local/bin/python3.6
Using base prefix '/Library/Frameworks/Python.framework/Versions/3.6'
New python executable in /Users/nuhil/mynewenvironment/bin/python3.6
Also creating executable in /Users/nuhil/mynewenvironment/bin/python
Installing setuptools, pip, wheel...done.
```
Now, activate the new environment and check it's Python's version and identity,
```sh
Nuhils-MacBook-Pro:~ nuhil$ cd mynewenvironment/
Nuhils-MacBook-Pro:mynewenvironment nuhil$ source bin/activate

(mynewenvironment) Nuhils-MacBook-Pro:mynewenvironment nuhil$ python
Python 3.6.0 (v3.6.0:41df79263a11, Dec 22 2016, 17:23:13) 
[GCC 4.2.1 (Apple Inc. build 5666) (dot 3)] on darwin
Type "help", "copyright", "credits" or "license" for more information.
>>>
```
Here, we can clearly see that, this environment's Python is actually a Python3.6 that we wanted it to be. Sure, we can also check whether this is an isolated Python or not. Also, we can check which is the base of this Python interpreter.
```sh
(mynewenvironment) Nuhils-MacBook-Pro:mynewenvironment nuhil$ which python
/Users/nuhil/mynewenvironment/bin/python

(mynewenvironment) Nuhils-MacBook-Pro:mynewenvironment nuhil$ ls -al
total 16
drwxr-xr-x   7 nuhil  staff   238 Oct  5 05:59 .
drwxr-xr-x+ 56 nuhil  staff  1904 Oct  5 05:59 ..
lrwxr-xr-x   1 nuhil  staff    56 Oct  5 05:59 .Python -> /Library/Frameworks/Python.framework/Versions/3.6/Python
drwxr-xr-x  16 nuhil  staff   544 Oct  5 05:59 bin
drwxr-xr-x   3 nuhil  staff   102 Oct  5 05:59 include
drwxr-xr-x   3 nuhil  staff   102 Oct  5 05:59 lib
-rw-r--r--   1 nuhil  staff    60 Oct  5 05:59 pip-selfcheck.json
```
and lastly, as its a new virtual environment and totally separated from the earlier one named `myenvironment` , is should show us nothing but some default package installed in a fresh mode ( I mean it should not contain the `numpy`  package that we installed on `myenvironment`  environment).
```sh
(mynewenvironment) Nuhils-MacBook-Pro:mynewenvironment nuhil$ pip list
pip (9.0.1)
setuptools (36.5.0)
wheel (0.30.0)
```
## Managing an Environment
As we made a new virtual environment with our desired Python 3.6 and started again with a fresh ecosystem, let's delete the old virtual environment. Oh yes, its as simple as deleting a directory:
```sh
Nuhils-MacBook-Pro:~ nuhil$ rm -rf myenvironment/
```
As, I mentioned before, you are not supposed to put your actual app files inside the environment's folder. Environment is just an environment definition, it should not contain your actual files and scripts. So, by deleting that unnecessary environment folder, you can get rid off that messed up Python environment. Is not it easy to throw away a messed up virtual environment that throwing away a full OS?

In the next two posts, I will discuss about `conda`  & `venv`  for similar purpose :)

## Resources

* https://virtualenv.pypa.io/en/stable/

> **Do you love Watching than Reading?**  
[Subscribe](https://www.youtube.com/channel/UCJFY9iVRXTJu1SPVI_vRNDw) & Get Connected with my [YouTube](https://www.youtube.com/channel/UCJFY9iVRXTJu1SPVI_vRNDw) channel for Video version of all my Blog posts.