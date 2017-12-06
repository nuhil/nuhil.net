+++
languageCode = "bn-bd"
title = "Virtual Environment for Python Workspace Part 2/3 conda"
author = "Nuhil Mehdy"
categories = ["Python"]
tags = ["python", "virtual environment", "virtualenv", "conda"]
date = 2017-10-02T00:00:00-00:00
description = "How to create virtual environment in Python using conda."
featured = ""
featuredalt = "Python"
featuredpath = "//i.imgur.com/tfD0kY8.png"
linktitle = ""
type = "post"
+++

Hope you already got the idea behind the necessity of virtual environment in Python ecosystem in my [previous post](/blog/virtual-environment-for-python-workspace-part-1-3-virtualenv/). So, in this post I will directly go into the detail of `conda`  and its usage.

## What is conda?
Just like `virtualenv` , this is also a package, dependency & environment management tool. Unlike `virtualenv` , `conda`  can work not only with Python but also with R, Javascript, Ruby, Lua, Scala etc. But, we will only focus on Python ecosystem for the sake of this series.

There are some significant benefits of `conda`  over `virtualenv` . For example - in its default configuration, `conda`  can install and manage thousand of packages at repo.continuum.io that are built, reviewed and maintained by Anaconda. Also, `conda`  can be combined with Continous Integration tools for better test & deployment.

## How to install conda?
The easiest way to get `conda`  is to install `miniconda` . Yes, its sounds like Anaconda. But we don't need to install that big fat ready-made environment. Rather we can install `miniconda`  that will come with `conda`  as package manager and its dependencies and the Python. By the way,

> You do not need to uninstall other Python installations or packages in order to use conda. Even if you already have a system Python, another Python installation from a source such as the macOS Homebrew package manager and globally installed packages from pip such as pandas and NumPy, you do not need to uninstall, remove, or change any of them before using conda.

So, just download `miniconda`  from [here](https://conda.io/miniconda.html) and install in your system. You can choose either Python 2.X or Python 3.X version (I prefer to install `miniconda`  of Python 3.X version). We will talk about that very soon. The installer will add the `conda`  installation of Python to your PATH environment variable. To verify that `conda`  is installed successfully, issue the following command.
```sh
conda --version
```
## Creating Virtual Environment
Before creating an environment, please keep in mind that, there are two variants of the installer: Miniconda is Python 2.X based and Miniconda3 is Python 3.X based. Note that the choice of which Miniconda is installed only affects the root environment. Regardless of which version of Miniconda you install, you can still install both Python 2.x and Python 3.x based environments.

Suppose you installed Python 3.X version of Miniconda and then if you issue the following command to create an environment,
```sh
conda create -n myenv python
```
the environment will be created based on Python 3.X version. On the other hand if you issue the following command, it will create a virtual environment based on Python 2.X.
```sh
conda create -n mypy2env python=2
```
Anyway, for now, forget about the `mypy2env` . Let's activate the `myenv`  environment and start using that.

## Activating an Environment
To activate the new environment, run the appropriate command for your operating system:   

* Linux and macOS: `source activate myenv`
* Windows: `activate myenv`

As my `miniconda`  version was of Python 3.X version and I created the environment `myenv`  with default Python, so this environment is based on Python 3.X. We can also check that by activating and running the Python REPL in it, maybe. Just check out the following Terminal activity and hope you will get it :)
```sh
Nuhils-MacBook-Pro:~ nuhil$ source activate myenv

(myenv) Nuhils-MacBook-Pro:~ nuhil$ python
Python 3.6.2 |Continuum Analytics, Inc.| (default, Jul 20 2017, 13:14:59) 
[GCC 4.2.1 Compatible Apple LLVM 6.0 (clang-600.0.57)] on darwin
Type "help", "copyright", "credits" or "license" for more information.
>>>
```
Type `exit()`  in the above REPL to quit it and simply get back to the environment.

## Deactivating an Environment
Deactivating an environment is as simple as issuing the following command,
```sh
source deactivate
```
So, the above command will deactivate the `myenv`  environment. Oh, by the way, before deactivating, let's check which packages are installed in this new virtual environment by the following command:
```sh
(myenv) Nuhils-MacBook-Pro:~ nuhil$ conda list
# packages in environment at /Users/nuhil/miniconda3/envs/myenv:
#
certifi                   2016.2.28                py36_0  
openssl                   1.0.2l                        0  
pip                       9.0.1                    py36_1  
python                    3.6.2                         0  
readline                  6.2                           2  
setuptools                36.4.0                   py36_1  
sqlite                    3.13.0                        0  
tk                        8.5.18                        0  
wheel                     0.29.0                   py36_0  
xz                        5.2.3                         0  
zlib                      1.2.11                        0
```
Want to install packages in this virtual environment for your next project?

## Managing Packages in an Environment
If you want to install packages using the `conda`  package manager then it can be done simply by `conda install <packagename>` . For example, let's install the package `beautifulsoup4`  in the environment `myenv` :
```sh
conda install beautifulsoup4
```
A good thing about `conda`  package manager is that, if you don't find a package using `conda install`  then you can look into Anaconda.org which is another product of the same vendor of miniconda and Anaconda. For example, to install the package `bottleneck` , you can issue the following command:
```sh
conda install --channel https://conda.anaconda.org/pandas bottleneck
```
Keep in mind that, you have to search for the desired package in the Anaconda.org site and there you will get the appropriate installation command for `conda` .

## pip in conda
If you don't find a package in conda or in Anaconda.org, then still you can install the package inside this `conda`  virtual environment by `pip` . Using `pip`  will download and install the package from Python's official package repository [PyPI](https://pypi.python.org/pypi). For example, let's install `numpy`  in this virtual environment by the following command:
```sh
pip install numpy
```
Now, let's check the packages that are installed so far in the environment by the following command again:
```sh
conda list
```
which will show something like following:
```sh
(myenv) Nuhils-MacBook-Pro:~ nuhil$ conda list
# packages in environment at /Users/nuhil/miniconda3/envs/myenv:
#
beautifulsoup4            4.6.0                    py36_0  
certifi                   2016.2.28                py36_0  
numpy                     1.13.3                    <pip>
openssl                   1.0.2l                        0  
pip                       9.0.1                    py36_1  
python                    3.6.2                         0  
readline                  6.2                           2  
setuptools                36.4.0                   py36_1  
sqlite                    3.13.0                        0  
tk                        8.5.18                        0  
wheel                     0.29.0                   py36_0  
xz                        5.2.3                         0  
zlib                      1.2.11                        0
```
In the above output, we can see that both `beautifulsoup4`  & `numpy`  exist together, though we installed `beautifulsoup4`  using `conda`  from their repository and `numpy`  from PyPI using `pip` .

## Removing an Environment
Before removing any environment, you need to see all existing conda environments, right? For that, simply issue the following command which will show you all the existing virtual environments made by conda:
```sh
Nuhils-MacBook-Pro:~ nuhil$ conda info --envs
# conda environments:
#
myenv                    /Users/nuhil/miniconda3/envs/myenv
mypy2env                 /Users/nuhil/miniconda3/envs/mypy2env
root                  *  /Users/nuhil/miniconda3
```
Lets, remove the `mypy2env`  which we don't want to use.
```sh
conda remove --name mypy2env --all
```
## Sharing Environment to Other
Say, you have prepared a very good Python environment with all the necessary packages installed in it and made sure that the environment is working fine for your project/app. Now, you want to share this ready-made environment with your friend who is struggling to prepare such an environment where he wants to work on the same Python project/app. Yes, you can do that by simply exporting your environment configuration in a file and sharing that file with your friend.

First, you need to activate the environment you want to share. Then, to export our `myenv`  environment's configuration, issue the following command:
```sh
(myenv) Nuhils-MacBook-Pro:~ nuhil$ conda env export > environment.yml
```
So, the shareable file is called `environment.yml`  and want to see whats in this file? It should contain something like following:
```sh
name: myenv
channels:
- defaults
dependencies:
- beautifulsoup4=4.6.0=py36_0
- certifi=2016.2.28=py36_0
- openssl=1.0.2l=0
- pip=9.0.1=py36_1
- python=3.6.2=0
- readline=6.2=2
- setuptools=36.4.0=py36_1
- sqlite=3.13.0=0
- tk=8.5.18=0
- wheel=0.29.0=py36_0
- xz=5.2.3=0
- zlib=1.2.11=0
- pip:
  - numpy==1.13.3
prefix: /Users/nuhil/miniconda3/envs/myenv

```
Pretty self-explanatory, right? Now, you can share this file to your friend and if your friend wants to prepare such a ready-made virtual environment, then he needs to install `conda`  first and the issue the following command:
```sh
conda env create -f environment.yml
```

> conda is the package manager. Anaconda is a set of about a hundred packages including conda, numpy, scipy, ipython notebook, and so on. Did you know, Once you have Miniconda, you can easily install Anaconda into it with `conda install anaconda` ?

## Resources

* https://conda.io/docs/user-guide/getting-started.html

