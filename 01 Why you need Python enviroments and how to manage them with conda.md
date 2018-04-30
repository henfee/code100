# [Why you need Python environments and how to manage them with Conda](https://medium.freecodecamp.org/why-you-need-python-environments-and-how-to-manage-them-with-conda-85f155f4353c)
---
![Gergely Szerovay](https://cdn-images-1.medium.com/fit/c/120/120/1*r_CaT9oEabzWJZtcJJN3WA.jpeg)

* Author: Gergely Szerovay

* Date: Feb 21, 2018

* Source: https://medium.freecodecamp.org/why-you-need-python-environments-and-how-to-manage-them-with-conda-85f155f4353c
---

---
![This is how a perfect Python environment looks like ;)](https://cdn-images-1.medium.com/max/1600/1*KhP3BJNqy4MC8GPfUz4r-Q.jpeg)

I have over two decades of professional experience as a developer, I know a wide variety of frameworks and programming languages, and one of my favorites is Python. I’ve been teaching it for quite some time now, and according to my experience, **establishing Python environments** is a **challenging topic**.

Thus, my main motivation for writing this article was to help current and potential Python users to have a **better understanding** of how to manage such environments.

If you’ve opened this article, chances are that you already know what Python is, why it is a great tool, and you even have a Python installed on your computer.

So **why exactly do you need Python environments?** You might ask: shouldn’t I just install the latest Python version?

## **Why you need multiple Python environments**

When you start learning Python, it is a good starting point to install the newest Python version with the latest versions of the packages you need or want to play around with. Then, most likely, you immerse yourself in this world, and download Python applications from GitHub, Kaggle or other sources. These applications may need other versions of Python/packages than the ones you have been currently using.

In this case, you need to set up different so-called **environments**.

Aside from this situation, there are more use cases when having additional environments might come in handy:

* You have an **application** (developed by yourself or by someone else) that **once worked** beautifully. But now you’ve tried to run it, and it is not working. Perhaps one of the packages is no longer compatible with the other parts of your program (due to the so-called **breaking changes**). A possible solution is to set up a new environment for you application, that contains the Python version and the packages that are completely compatible with your application.
* You are **collaborating with someone else**, and you want to make sure that your application is working on your team member’s computer, and vice versa, so you can also set up an environment for your co-worker’s application(s).
* You are **delivering an application to your client**, and again, you want to make sure that it is working smoothly on your client’s computer.

An environment consists of a certain Python version and some packages. Consequently, if you want to **develop or use applications with different Python or package version requirements**, you need to set up different environments.

Now that we’ve discussed why environments are useful, let’s dive in and talk about some of the most important aspects of managing them.

## Package and environment managers

The two most popular tools for setting up environments are:

* **[PIP](https://pip.pypa.io/en/stable/)** (a Python package manager; funnily enough, it stands for “Pip Installs Packages”) with [virtualenv](https://virtualenv.pypa.io/en/stable/) (a tool for creating isolated environments)
* **Conda** (a package and environment manager)

In this article, I cover how to use **Conda**. I prefer it because:

1. **Clear Structure**: It is easy to understand its directory structure
2. **Transparent File Management**: It doesn’t install files outside its directory
3. **Flexibility**: It contains a lot of packages (PIP packages are also installable into Conda environments)
4. **Multipurpose**: It is not only for managing Python environments and packages — you can also use it for R (a programming language for statistical computing)

At the time of writing this article, I use the 4.3.x versions of Conda, but the new 4.4.x versions are also available.

In the case of Conda 4.4, there have been recent changes affecting Linux/Mac OS X users. They are described in this [changelog entry](https://github.com/conda/conda/blob/master/CHANGELOG.md#recommended-change-to-enable-conda-in-your-shell).

## How to choose an appropriate Conda download option

**Installing your Conda system** is a bit more complicated than downloading a nice picture from Unsplash or buying a new ebook. Why is that?

### 1. Installer

Currently, there are 3 **different installers**:
* [Anaconda](https://www.anaconda.com/download/) (free)
* [Miniconda](https://conda.io/miniconda.html) (free)
* [Anaconda Enterprise platform](https://www.anaconda.com/enterprise/)(it is a commercial product that allows organizations to apply Python and R in enterprise environments)

Let’s take a closer look at the free tools, **Anaconda** and **Miniconda**. Now, what are the main differences between these two?

What are the things they share in common? They both set up on your computer

* the **Conda** (the package & environment management system) and
* the so-called **“root environment”** (more on that a bit later).

As for the main differences, **Miniconda** requires about 400MB disk space, and it contains only a few basic packages.

The **Anaconda** installer requires about 3GB disk space, and it installs over 150 scientific packages (for example, packages for statistics and machine learning). It also sets up the Anaconda Navigator, a GUI tool that helps you manage Conda environments and packages.

**I prefer Miniconda**, since I’ve never used most of the packages that are included in Anaconda by default. Another reason is that applying Miniconda allows for a smoother duplication of the environment (for example, if I want to use it on a different computer as well), since I only install the packages required by my app(s) on both computers.

From now on, I’m going to describe how Miniconda works (in the case of using Anaconda, the process is almost the same).

### 2–3. Platform (operating system and bit-count)
In addition to these 3 different installers, there are also subtypes based on bit-count: **32- and 64-bit** installers. And of course these also have subtypes for the different operating systems: **Windows, Linux, and Mac OS X** (except that the Mac OS X version is 64-bit only).

In this article, I focus on the **Windows** version (the Linux and the Mac OS X versions are only slightly different. For instance the path of the installation folders and some command line commands differ).

**So 32-bit or 64-bit?**

If you have a 64-bit operating system (OS) with 4GB RAM or more, you should install the 64-bit version. Additionally, you might need a 64-bit installer if the packages you are planning to apply require the 64-bit versions of Python. For instance, if you want to use TensorFlow — more precisely, the official so-called binaries — you need a 64-bit OS and Python version.

If you have a 32-bit OS or you are planning to utilize packages that only have 32-bit versions, the 32-bit version is the good option for you.

### 4. Python version (for the root environment)

If these 3 dimensions aren’t enough (installers, 32/64-bit, and operating systems), there is a 4th one based on the **different Python versions** (included in the installer — and consequently, in the root environment)!

So let’s talk a bit about the different **available Python versions**.

Currently, your options are **version 2.7** or **version 3.x** (at the time of writing this article, it’s 3.6) for the Python that is inside the root environment. For the additional environments, you can choose any version — ultimately, this is why you create environments in the first place: to easily switch between the different environments and versions.

**So 2.7 or 3.x version Python for my root environment?**

Let me help you decide it really quickly:

Since the **3.x** is newer, this should be your default choice. (The 2.7 version is a legacy version, it was released in 2010, and there won’t be newer 2.7 major releases for it, only fixes.)

However, if

* you have mostly **2.7 code** (you made or utilize applications using the 2.7 versions) or
* you need to **use packages that don’t have Python 3.x versions**,

you should install a Python 2.7-based root environment.

You might ask that: **why don’t I just create two environments based on these two 2.7 and 3.x versions?** I’m glad that you asked. The reason for that is that your root environment is the one that is created during the installation process and it’s **activated by default**.

I’ll explain in one of the following sections how you can activate an environment, but basically it means that the root environment is the more easily accessible one, so **carefully selecting your root environment** will make your workflow more efficient.

Throughout the installation process, Miniconda will let you change some **options set by default** (for example you can check/uncheck some checkboxes). When you install Conda for the first time, I recommend that you leave these options intact (except for the path of the installation directory).

![Choosing an appropriate installer for Conda](https://cdn-images-1.medium.com/max/1600/1*4MbAW6APDD_GT14vaRkKQQ.jpeg)

I’d like to mention one more thing here. While you can have multiple environments that contain different versions of Python at the same time on the same computer, you can’t set up **32- and 64-bit environments** using the same Conda management system. It is possible to **mix them somehow**, but it is not that easy, so I’m going to devote a separate article to this topic.

## Python environments: root and additional

So now you’ve picked an appropriate installer for yourself, well done! Now let’s take a look at the different types of environments and how they are created.

Miniconda sets up two things for you: **Conda** and the **root environment**.

The process looks like this: the installer installs Conda first, which is — as I already mentioned — the package and environment management tool. Then, Conda creates **a root environment that contains two things**:

* a certain version of Python and
* some basic packages.

Next to the root environment, you can create as many **additional environments** as you want. And the whole point is that these additional environments **can contain different versions of Pythons and other packages**. So it means that, for example, if your precious little application is not working anymore in the newest, state-of-the-art environment you’ve just set up, you can always go “back” and use some another version(s) of some packages (including Python— Python itself is a package, more on that later).

As I already summarized at the beginning of the article, the main use cases of applying an additional environment are these:

* You **develop applications** with different Python or package version requirements
* You **use applications** with different Python or package version requirements
* You **collaborate** with other developers
* You create Python applications **for clients**

![Root and additional environments](https://cdn-images-1.medium.com/max/1600/1*0qVCJMcjaKZEcFEyHDj2yg.jpeg)

Before diving into the basics of environment management, let’s take a look at your Conda system’s directory structure.

## Directory structure

As I mentioned above, the Conda system is installed into a single directory. In my example this directory is: ```D:\Miniconda3-64\```. It contains the root environment and two important directories (the other directories are irrelevant for now):

* ```\pkgs``` (it contains the cached packages in compressed and uncompressed formats)
* ```\envs``` (it contains the environments — except for the root environment — in separate subdirectories)

The most significant **executable files** and directories inside a Conda environment (placed in the ```\envs\environmentname``` directory) are:

* ```\python.exe``` — the Python executable for command line applications. So for instance, if you are in the directory of the ```Example App```, you can execute it by: ```python.exe exampleapp.py```
* ```\pythonw.exe``` — the Python executable for GUI applications, or completely UI-less applications
* ```\Scripts``` — executables that are parts of the installed packages. Upon activation of an environment, this directory is added to the system path, so the executables become available without their full path
* ```\Scripts\activate.exe``` — activates the environment

And if you’ve installed Jupyter, this is also an important file:
* ```\Scripts\jupyter-notebook.exe``` — Jupyter notebook launcher (part of the jupyter package). In short, Jupyter Notebook creates so-called notebook documents that contain executable parts (for example Python) and human-readable parts as well. It’d take another article to get into it in more detail.

So now you should have at least one Python environment successfully installed on your computer. But how can you start utilizing it? Let’s take a closer look.

## GUI vs. Command line (Terminal)

As I mentioned above, the Anaconda installer also installs a graphical user interface (GUI) tool called Anaconda Navigator. I also pointed out that I prefer using Miniconda, and that does not install a GUI for you, so you need to use text-based interfaces (for example command line tools or the Terminal).

In this article, I focus on the **command line tools** (Windows). And while I concentrate on the Windows version, these examples can be applied to Linux and Mac OS X as well, only the path of the installation folders and some command line commands differ.

To **open the command line**, select “Anaconda 32-bit” or “Anaconda 64-bit” (depending on your installation) in the Windows’s Start menu, then choose “Anaconda Prompt”.

I recommend reading through the official [Conda cheat sheet](https://conda.io/docs/_downloads/conda-cheatsheet.pdf) (pdf), as it contains the command differences between Windows and Mac OS X/Linux, too.

In the following sections, I’m going to give you some **examples of the basic commands**, indicating their results as well. Hopefully these will help you better manage your new environment.

## Managing environments
### Adding a new environment

To create a new environment named, for instance ```mynewenv``` (you can name it what ever you like), that includes, let’s say, a Python version 3.4., run:

```
conda create --name mynewenv python=3.4
```

You can change an environment’s Python version by using the package management commands I describe in the next section.

### Activating and leaving (deactivating) an environment

Inside a new Conda installation, the root environment is activated by default, so you can use it without activation.

In other cases, if you want to use an environment (for instance manage packages, or run Python scripts inside it) you need to first ```activate``` it.

Here is a **step by step guide** of the activation process:

First, open the command line (or the Terminal on Linux/Mac OS X). To activate the mynewenv environment, use the following commands depending on the operating system you have:

* on Windows:
```
activate mynewenv
```
* On Linux or Mac OS X:
```
source activate mynewenv
```
The **command prompt changes** upon the environment’s activation. It becomes, for example, ```(mynewenv) C:\>``` or ```(root) D:\>```, so as a result of the activation, it now contains the active environment’s name.

The directories of the active environment’s executable files are added to the system path (this means that you can now access them more easily). You can leave an environment with this command:

```
deactivate
```

On Linux or Mac OS X, use this one:

```
source deactivate
```

According to the official Conda documentation, in Windows it is a good practice to deactivate an environment before activating another.

It needs to be mentioned that upon deactivating an environment, the root environment becomes active automatically.

To **list out the available environments** in a Conda installation, run:
```
conda env list
```

Example result:

```
# conda environments:
#
mynewenv                 D:\Miniconda\envs\mynewenv
tensorflow-cpu           D:\Miniconda\envs\tensorflow-cpu
root                  *  D:\Miniconda
```

Thanks to this command, you can list out all your environments (the root and all the additional ones). The **active** environment is marked with an **asterisk** (at each given moment, there can be only one active environment).

## How do you learn the version of your Conda?

It can be useful to check **what version of Conda you are using**, and also what are the other parameters of your environment. I’m going to show you below how to easily list out this information.
To get the Conda version of the currently active environment, run this command:
```
conda --version
```
Example result:
```
conda 4.3.33
```
To get a **detailed list of information** about the environment, for instance:

* Conda version,
* platform (operating system and bit count — 32- or 64-bit),
* Python version,
* environment directories,

run this command:
```
conda info
```

Example result:
```
Current conda install:
platform : win-64
          conda version : 4.3.33
       conda is private : False
      conda-env version : 4.3.33
    conda-build version : not installed
         python version : 3.6.3.final.0
       requests version : 2.18.4
       root environment : D:\Miniconda  (writable)
    default environment : D:\Miniconda\envs\tensorflow-cpu
       envs directories : D:\Miniconda\envs
                          C:\Users\sg\AppData\Local\conda\conda\envs
                          C:\Users\sg\.conda\envs
          package cache : D:\Miniconda\pkgs
                          C:\Users\sg\AppData\Local\conda\conda\pkgs
           channel URLs : https://repo.continuum.io/pkgs/main/win-64
                          https://repo.continuum.io/pkgs/main/noarch
                          https://repo.continuum.io/pkgs/free/win-64
                          https://repo.continuum.io/pkgs/free/noarch
                          https://repo.continuum.io/pkgs/r/win-64
                          https://repo.continuum.io/pkgs/r/noarch
                          https://repo.continuum.io/pkgs/pro/win-64
                          https://repo.continuum.io/pkgs/pro/noarch
            config file : C:\Users\sg\.condarc
             netrc file : None
           offline mode : False
             user-agent : conda/4.3.33 requests/2.18.4 CPython/3.6.3 Windows/10 Windows/10.0.15063
          administrator : False
```

Now you know some basic commands for managing your environment. Let’s take a look at managing the packages inside the environment.

## Managing packages

Depending on the installer you chose, you’re going to end up with some basic (in case of using Miniconda) or a lot of (in case of using Anaconda) packages to start with. But what happens if you need

* a **new package** or
* **another version** of an already installed package?

Conda — your environment and package management tool — will come to the rescue. Let’s look at this in more detail.

## Package channels

**Channels are the locations** of the repositories (on the illustration I call them storages) **where Conda looks for packages**. Upon Conda’s installation, Continuum’s (Conda’s developer) channels are set by default, so without any further modification, these are the locations where your Conda will start searching for packages.

**Channels exist in a hierarchical order**. The channel with the highest priority is the first one that Conda checks, looking for the package you asked for. You can change this order, and also add channels to it (and set their priority as well).

It is a **good practice to add a channel** to the channel list as **the lowest priority item**. That way, you can include “special” packages that are not part of the ones that are set by default (~Continuum’s channels). As a result, you’ll end up with all the default packages — without the risk of overwriting them by a lower priority channel — AND that “special” one you need.

![This is how channels work](https://cdn-images-1.medium.com/max/1600/1*L6Va-HCq5mvifsDtjFbxlw.jpeg)


To install a certain package that cannot be found inside these default channels, you can search for that **“special” package on this [website](https://anaconda.org/anaconda/repo)**. Not all packages are available on all platforms (=operating system & bit count, for example 64-bit Windows), however, you can narrow down your search to a specific platform. If you find a channel that contains the package you’re looking for, you can append it to your channel list.

To **add a channel** (named for instance newchannel) with the **lowest priority**, run:
```
conda config --append channels newchannel
```

To add a channel (named newchannel) with the **highest priority**, run:
```
conda config --prepend channels newchannel
```

It needs to be mentioned that in practice you’ll most likely set channels with the lowest priority. For a beginner, adding a channel with the highest priority is an edge case.

To **list out the active channels and their priorities**, use the following command:

```
conda config --get channels
```

Example result:
```
--add channels 'conda-forge'   # lowest priority
--add channels 'rdonnelly'
--add channels 'defaults'   # highest priority
```

There is one more aspect that I’d like to summarize here. If **multiple channels contain a package**, and one channel contains a newer version than the other one, the channels’ hierarchical order determines which one of these two versions are going to be installed, even if the higher priority channel contains the older version.

![The version inside the higher priority channel is going to be installed](https://cdn-images-1.medium.com/max/1600/1*MlQ3bR4i6tYs_Jx-DEVPWg.jpeg)

### Searching, installing and removing packages

To list out all the installed packages in the currently active environment, run:
```
conda list
```

The command results in a list of the matching package names, versions, and channels:
```
# packages in environment at D:\Miniconda:
#
asn1crypto                0.22.0           py36h8e79faa_1
bleach                    1.5.0                     <pip>
ca-certificates           2017.08.26           h94faf87_0
...
wheel                     0.29.0           py36h6ce6cde_1
win_inet_pton             1.0.1            py36he67d7fd_1
wincertstore              0.2              py36h7fe50ca_0
yaml                      0.1.7            vc14hb31d195_1  [vc14]
```

To **search** for **all the available versions of a certain package**, you can use the search command. For instance, to list out all the versions of the seaborn package (it is a tool for data visualization), run:
```
conda search -f seaborn
```
Similarly to the conda listcommand, this one results in a list of the matching package names, versions, and channels:

```
Fetching package metadata .................
seaborn           0.7.1                    py27_0  conda-forge
                  0.7.1                    py34_0  conda-forge
                  0.7.1                    py35_0  conda-forge
...
                  0.8.1            py27hab56d54_0  defaults
                  0.8.1            py35hc73483e_0  defaults
                  0.8.1            py36h9b69545_0  defaults
```

To **install** a package (for instanceseaborn) that is **inside a channel that is on your channel list**, run this command (if you don’t specify which version you want, it’ll automatically install the latest available version from the highest priority channel):

```
conda install seaborn
```

You can also **specify the package’s version**:

```
conda install seaborn=0.7.0
```

To install a package (for example ```yaml```— that is, btw. a YAML parser and emitter) from a channel (for instance a channel named ```conda-forge```), that is **inside a channel that is not on your channel list**, run:

```
conda install -c conda-forge yaml
```

To **update all the installed packages** (it only affects the active environment), use this command:

```
conda update
```

To **update one specific package**, for example the ```seaborn``` package, run:

```
conda update seaborn
```

To **remove** the ```seaborn``` package, run:

```
conda remove seaborn
```

There is one more aspect of managing packages that I’d like to cover in this article. If you don’t want to deal with compatibility issues (breaking changes) caused by a new version of one of the packages you use, you can **prevent that package from updating**. As I mentioned above, if you run the ```conda update``` command, all of your installed packages are going to be updated, so basically it is about creating an “exception list”. So how can you do this?

### Prevent packages from updating (pinning)

Create a file named ```pinned``` in the environment’s ```conda-meta``` directory. Add the list of the packages that you don’t want to be updated to the file. So for example, to force the ```seaborn``` package to the 0.7.x branch and lock the ```yaml``` package to the 0.1.7 version, add the following lines to the file named pinned:

```
seaborn 0.7.*
yaml ==0.1.7
```

### Changing an environment’s Python version

And how can you **change the Python version of an environment?**

**Python is also a package.** Why is that relevant for you? Because you’re going to use the same command for replacing the currently installed version of Python with another version that you use when you replace any other package with another version of that same package.

First, you should list out the available Python versions:

```
conda search -f python
```

Example result (the list contains the available versions and channels):

```
Fetching package metadata .................
python   2.7.12     0  conda-forge
         2.7.12     1  conda-forge
         2.7.12     2  conda-forge
...
3.6.3      h3b118a2_4  defaults
         3.6.4      h6538335_0  defaults
         3.6.4      h6538335_1  defaults
```

To **replace the current Python version** with, for example, 3.4.2, run:

```
conda install python=3.4.2
```

To **update the Python version** to the latest version of its branch (for instance updating the 3.4.2 to the 3.4.5 from the 3.4 branch), run:

```
conda update python
```

### Adding PIP packages

Towards the beginning of this article, I recommended using Conda as your package and environment manager (and not PIP). And as I mentioned above, **PIP packages are also installable into Conda environments**.

Therefore, if a package is unavailable through the Conda channels, you can try to install it from the [PyPI package index](https://pypi.python.org/pypi). You can do this by using the ```pip``` **command** (this command is made available by the Conda installer by default, so you can apply it in any active environment). For instance if you want to install the ```lightgbm``` package (it is a gradient boosting framework), run:

```
pip install lightgbm
```

## Summary

So let’s wrap this up. I know that it seems quite complicated — and it is, in fact, complicated. However, **utilizing environments will save you a lot of trouble**.

In this article, I’ve summarized how you can:

* choose an appropriate **Conda installer** for yourself
* create **additional environments** (next to the root environment)
* **add or replace packages** (and I also explain how channels work)
* manage your **Python version(s)**

There are many more aspects in the area of Python environment management, so **please let me know what aspects you find most challenging**. Also let me know if you have some good practices that I don’t mention here. I’m curious about your workflow, so please feel free to share in the response section below if you have any **suggestions!**

## Recommended Articles

If you’re interested in this topic, I encourage you to check out these articles as well. Thanks for these great resources [Michael Galarnyk](https://medium.com/@GalarnykMichael), [Dries Cronje](https://medium.com/@dries139), [Ryan Abernathey](https://medium.com/@rabernat), [Sanyam Bhutani](https://medium.com/@init_27), [Jason Brownlee](https://medium.com/@jason.brownlee05) and [Jake Vanderplas](https://github.com/jakevdp).

---
# Translate into Chinese:
---
# [为什么需要Python环境，以及如何使用Conda来管理它们?](https://medium.freecodecamp.org/why-you-need-python-environments-and-how-to-manage-them-with-conda-85f155f4353c)
---
![Gergely Szerovay](https://cdn-images-1.medium.com/fit/c/120/120/1*r_CaT9oEabzWJZtcJJN3WA.jpeg)

* 作者: Gergely Szerovay

* 发表日期: 2018-02-21

* 源文件: https://medium.freecodecamp.org/why-you-need-python-environments-and-how-to-manage-them-with-conda-85f155f4353c
---

---
![This is how a perfect Python environment looks like ;)](https://cdn-images-1.medium.com/max/1600/1*KhP3BJNqy4MC8GPfUz4r-Q.jpeg)


作为一名开发人员，我有超过20年的专业经验，我知道各种各样的框架和编程语言，我最喜欢的是Python。我已经教了很长时间了，根据我的经验，**建立Python环境是一个具有挑战性的话题**。

因此，我撰写本文的主要动机是帮助当前和潜在的Python用户对如何管理这样的环境有一个更好的理解。

如果您已经打开了这篇文章，很可能您已经知道Python是什么，为什么它是一个伟大的工具，您甚至在您的计算机上安装了Python。

那么 **为什么需要Python环境呢?** 你可能会问:我是不是应该安装最新的Python版本?

## **为什么需要多个Python环境**

当您开始学习Python时，安装最新版本的Python版本是一个很好的起点，您需要或想要使用的软件包的最新版本。然后，很有可能，您将自己沉浸在这个世界中，并从GitHub、Kaggle或其他来源下载Python应用程序。这些应用程序可能需要其他版本的Python包，而不是您目前使用的版本。

在这种情况下，您需要设置不同的所谓 **环境**。

除了这种情况之外，还有更多的用例，当有额外的环境可能会派上用场:

但是现在你试着去运行它，它没有工作。也许其中一个软件包不再与程序的其他部分兼容(由于所谓的 **中断更改**)。一个可能的解决方案是为您的应用程序设置一个新的环境，其中包含Python版本和与您的应用程序完全兼容的包。
* **与他人合作**，你需要确保你的应用程序在你的团队成员的电脑上工作，反之亦然，所以你也可以为你的同事的应用设置一个环境。
* **将一个应用程序交付给你的客户**，并且再次，你要确保它在你的客户的电脑上运行顺畅。

环境由特定的Python版本和一些包组成。因此，如果您想要开发或使用具有不同Python或包版本需求的应用程序**，您需要设置不同的环境。

既然我们已经讨论了为什么环境是有用的，那么让我们深入讨论一下管理它们的一些最重要的方面。

## 包和环境管理器

设置环境最常用的两种工具是:

* **[Pip](https://pip.pypa.io/en/stable/)** (Python包管理器;有趣的是，它代表了“Pip安装包”)和[virtualenv](https://virtualenv.pypa.io/en/stable/)(创建隔离环境的工具)
* **Conda**(一个包和环境管理器)

在本文中，我将介绍如何使用 **Conda**。我喜欢它,因为:

1. **清晰的结构**:很容易理解它的目录结构。
2. **透明文件管理**:它不会在其目录外安装文件。
3. 所示。**灵活性**:它包含很多包(PIP包也可以安装到Conda环境中)
4. 所示。**Multipurpose**:它不仅用于管理Python环境和包——您还可以将其用于R(用于统计计算的编程语言)

在撰写本文时，我使用的是4.3.x版本的Conda，但是新的4.4,也有x版本。

在Conda 4.4的例子中，最近发生了影响Linux/Mac OS X用户的变化。它们在这个[changelog条目](https://github.com/conda/conda/conda/conda/blob/master/changelog.md)中被描述。

## 如何选择合适的Conda下载选项

**安装Conda系统** 要比从Unsplash下载一幅漂亮的图片或购买一本新电子书要复杂得多。这是为什么呢?

### 1. 安装程序

目前，有3种 **不同的安装程序**:
* [Anaconda](https://www.anaconda.com/download/)(免费)
* [Miniconda](https://conda.io/miniconda.html)(免费)
* [Anaconda Enterprise platform](https://www.anaconda.com/enterprise/)(它是一种商业产品，允许组织在企业环境中应用Python和R)

让我们仔细看看免费工具，**Anaconda** 和 **Miniconda**。那么，这两者之间的主要区别是什么呢?

他们有什么共同之处?他们都安装在你的电脑上。

*  **Conda**(包装及环境管理器)和
* 所谓的 **“根环境”**(稍后会详细说明)。

至于主要的区别，**Miniconda** 需要大约400MB的磁盘空间，它只包含几个基本的包。

**Anaconda** 安装程序需要大约3GB的磁盘空间，它安装超过150个科学包(例如，用于统计和机器学习的包)。它还设置了Anaconda导航器，一个帮助您管理Conda环境和包的GUI工具。

**我更喜欢Miniconda**，因为我从来没有使用过默认包含在Anaconda中的大多数包。另一个原因是，使用Miniconda可以使环境更加平滑(例如，如果我想在另一台计算机上使用它)，因为我只在两台计算机上安装我的应用程序所需要的软件包。

从现在开始，我将描述Miniconda是如何工作的(在使用Anaconda的情况下，这个过程几乎是一样的)。

### 2-3. 平台(操作系统和位数版本)

除了这3个不同的安装程序之外，还有基于bitcount的子类型:**32和64位** 安装程序。当然，它们也有不同操作系统的子类型:**Windows、Linux和Mac OS X**(除了Mac OS X版本只有64位)。

在本文中，我主要关注 **Windows** 版本(Linux和Mac OS X版本略有不同)。例如，安装文件夹的路径和一些命令行命令是不同的。

**32位或64位呢？**

如果您的64位操作系统(OS)带有4GB RAM或更多，您应该安装64位版本。另外，如果要应用的包需要64位版本的Python，那么您可能需要64位安装程序。例如，如果您想使用TensorFlow——更确切地说，是正式的所谓二进制文件——您需要一个64位OS和Python版本。

如果您有一个32位的操作系统，或者您计划使用只有32位版本的包，那么32位版本对您来说是很好的选择。

### 4. Python版本(用于根环境)

如果这三个维度还不够(安装程序、32/64位和操作系统)，那么就有一个基于**不同Python版本**的第4个版本(包括在安装程序中，因此，在根环境中)!

因此，让我们讨论一下不同的 **可用Python版本**。

目前，您的选项是 **版本2.7**或**3.x版本**(在撰写本文时，它是3.6)用于根环境中的Python。对于额外的环境，您可以选择任何版本——最终，这就是您首先创建环境的原因:在不同的环境和版本之间轻松切换。

**所以根环境是选择2.7或3.x版本Python？**。

让我来帮你快速决定:

自 **3.x** 是更新的，这应该是您的默认选择。(2.7版本是一个遗留版本，它是在2010年发布的，并且不会有更新的2.7版本，只有修复。)

然而,如果

* 您主要有 **2.7代码**(您使用2.7版本创建或使用应用程序)或
* 您需要 **使用没有Python 3.x包的版本**,

您应该安装一个基于Python 2.7的根环境。

您可能会问:**为什么我不创建两个基于这两个2.7和3.x版本的环境呢**？我很高兴你问了这个问题。原因是，您的根环境是在安装过程中创建的，并且在缺省情况下是激活的。

我将在以下几节中解释如何激活环境，但基本上这意味着根环境更容易访问，所以 **仔细选择根环境** 会使您的工作流程更高效。

在整个安装过程中，Miniconda将允许您更改默认 **设置的一些选项**(例如，您可以检查/取消一些复选框)。当您第一次安装Conda时，我建议您保留这些选项(除了安装目录的路径)。

![为Conda选择合适的安装程序](https://cdn-images-1.medium.com/max/1600/1*4MbAW6APDD_GT14vaRkKQQ.jpeg)

我想再提一件事。虽然您可以在同一台计算机上同时拥有多个包含不同版本Python的环境，但您不能使用相同的Conda管理系统来设置 **32和64位环境**。有可能把它们混在一起，但这并不容易，所以我打算把一篇单独的文章写在这个主题上。

## Python环境:根和附加

所以现在您已经为自己选择了一个合适的安装程序，做得好！现在让我们来看看不同类型的环境以及它们是如何创建的。

Miniconda为您设置了两件事:**Conda** 和 **根环境**。

这个过程看起来是这样的:安装程序首先安装Conda，这是我已经提到过的包和环境管理工具。然后，Conda创建 **根环境，其中包含两个内容**:

* 特定版本的Python和
* 一些基本的软件包。

在根环境的旁边，您可以创建尽可能多的 **附加环境**。重点是这些额外的环境 **可以包含不同版本的python和其他包**。因此，这意味着，例如，如果您的宝贵的小应用程序不再在最新的、最先进的环境中工作，您就可以“返回”，并使用一些包的其他版本(包括Python - Python本身就是一个包，稍后将详细介绍)。

正如我在文章开头已经总结的，应用额外环境的主要用例如下:

* **使用不同的Python或包版本要求开发应用程序**。
* **使用不同的Python或包版本需求的应用程序**。
* 与其他开发人员 **合作**。
* 为 **客户** 创建Python应用程序。

![根和额外的环境](https://cdn-images-1.medium.com/max/1600/1*0qVCJMcjaKZEcFEyHDj2yg.jpeg)

在深入了解环境管理的基本知识之前，让我们先看看您的Conda系统的目录结构。

## 目录结构

如上所述，Conda系统被安装到一个目录中。在我的例子中，这个目录是:``` D:\Miniconda3-64\ ```。它包含根环境和两个重要的目录(其他目录现在不相关):

* ```\pkgs```(它包含压缩和未压缩格式的缓存包)
* ```\envs```(它包含了除根环境之外的环境——在单独的子目录中)

在Conda环境中最重要的 **可执行文件** 和目录(放置在```\envs\环境名称```目录)中:

* ```\python.exe``` —命令行应用程序的Python可执行文件。因此，例如，如果您在“示例应用程序”的目录中，您可以通过以下方式执行:```python.exe exampleapp.py```
* ```\pythonw.exe``` -用于GUI应用程序的Python可执行文件，或完全没有ui的应用程序。
* ``` \Scripts``` -可执行文件，是安装的软件包的一部分。在激活环境时，该目录被添加到系统路径中，因此可执行程序在没有完整路径的情况下可用。
* ```\Scripts\activate.exe``` -激活环境。

如果你安装了Jupyter，这也是一个重要文件:
* ```\Scripts\jupyter-notebook.exe``` - Jupyter笔记本启动器(Jupyter包的一部分)。简而言之，Jupyter笔记本创建了所谓的笔记本文档，其中包含可执行部分(例如Python)和人类可读的部分。要更详细地了解它需要另一篇文章。

因此，现在应该至少在计算机上成功安装了一个Python环境。但是你如何开始利用它呢？让我们仔细看看。

## GUI vs 命令行(终端)

正如我上面提到的，Anaconda安装程序还安装了一个名为Anaconda Navigator的图形用户界面(GUI)工具。我还指出，我更喜欢使用Miniconda，它不会为您安装GUI，因此您需要使用基于文本的接口(例如命令行工具或终端)。

在本文中，我主要关注 **命令行工具** (Windows)。当我专注于Windows版本时，这些例子也可以应用到Linux和Mac OS X上，只有安装文件夹和一些命令行命令的路径不同。

打开 **命令行**，在Windows开始菜单中选择“Anaconda 32位”或“Anaconda 64位”(取决于您的安装)，然后选择“Anaconda Prompt”。

我建议阅读官方的[Conda cheatsheet](https://conda.io/docs/_downloads/conda-cheatsheet.pdf)，因为它包含了Windows和Mac OS X/Linux之间的命令差异。

在下面的部分中，我将给出一些基本命令的示例，并说明它们的结果。希望这些能够帮助您更好地管理您的新环境。

## 管理环境

### 添加新环境

要创建一个名为```mynewenv```的新环境(您可以将其命名为您喜欢的名称)，包括Python 3.4版本。运行:


```
conda create --name mynewenv python=3.4
```

您可以使用我在下一节描述的包管理命令来更改环境的Python版本。

### 激活和离开(停用)一个环境。

在一个新的Conda安装中，根环境是默认激活的，所以您可以在不激活的情况下使用它。

在其他情况下，如果您想要使用环境(例如管理包，或者在其中运行Python脚本)，您需要首先“激活”它。

以下是激活过程的步骤指南:

首先，打开命令行(或Linux/Mac OS X上的终端)。要激活mynewenv环境，使用以下命令，具体操作系统如下:

* 在Windows中:

```
activate mynewenv
```

* 在Linux或Mac OS X中:

```
source activate mynewenv
```

命令提示符更改了环境的激活。例如，它变成了```(mynewenv) C:\> ```或```(root) D:\> ```，所以作为激活的结果，它现在包含了活动环境的名称。

活动环境的可执行文件的目录被添加到系统路径中(这意味着您现在可以更容易地访问它们)。您可以使用以下命令离开环境:

```
deactivate
```

在Linux或Mac OS X上，使用这个:

```
source deactivate
```

根据官方的Conda文档，在Windows中，在激活另一个环境之前禁用环境是一个很好的做法。

需要指出的是，在停用一个环境时，根环境会自动激活。

要**在Conda安装中列出可用的环境**，运行:

```
conda env list
```


结果示例:

```
# conda environments:
#
mynewenv                 D:\Miniconda\envs\mynewenv
tensorflow-cpu           D:\Miniconda\envs\tensorflow-cpu
root                  *  D:\Miniconda
```

由于这个命令，您可以列出所有的环境(根和所有其他的环境)。**活动环境** 被标记为 **星号** (在每个给定时刻，只能有一个活动环境)。

## 您如何学习您的Conda版本?

检查 **您使用的版本以及您的环境的其他参数** 是很有用的。下面我将向您展示如何轻松地列出这些信息。
要获得当前活动环境的Conda版本，请运行以下命令:

```
conda --version
```

结果示例:

```
conda 4.3.33
```

获得 **有关环境的详细信息**，例如:

* Conda版本,
* 平台(操作系统和位数- 32或64位)，
* Python版本,
* 环境目录,

运行这个命令:

```
conda info
```

结果示例:

```
Current conda install:
platform : win-64
          conda version : 4.3.33
       conda is private : False
      conda-env version : 4.3.33
    conda-build version : not installed
         python version : 3.6.3.final.0
       requests version : 2.18.4
       root environment : D:\Miniconda  (writable)
    default environment : D:\Miniconda\envs\tensorflow-cpu
       envs directories : D:\Miniconda\envs
                          C:\Users\sg\AppData\Local\conda\conda\envs
                          C:\Users\sg\.conda\envs
          package cache : D:\Miniconda\pkgs
                          C:\Users\sg\AppData\Local\conda\conda\pkgs
           channel URLs : https://repo.continuum.io/pkgs/main/win-64
                          https://repo.continuum.io/pkgs/main/noarch
                          https://repo.continuum.io/pkgs/free/win-64
                          https://repo.continuum.io/pkgs/free/noarch
                          https://repo.continuum.io/pkgs/r/win-64
                          https://repo.continuum.io/pkgs/r/noarch
                          https://repo.continuum.io/pkgs/pro/win-64
                          https://repo.continuum.io/pkgs/pro/noarch
            config file : C:\Users\sg\.condarc
             netrc file : None
           offline mode : False
             user-agent : conda/4.3.33 requests/2.18.4 CPython/3.6.3 Windows/10 Windows/10.0.15063
          administrator : False
```

现在您了解了一些管理环境的基本命令。让我们看看如何管理环境中的包。

## 管理包

根据您选择的安装程序，您将以一些基本的(如使用Miniconda)或大量(以使用Anaconda)包作为开始。但是如果你需要的话会发生什么呢?

* **新包** 或
* **已经安装的包的另一个版本** ?

Conda -您的环境和包管理工具-将会来拯救。让我们更详细地看看这个。

### 包的频道

**频道是Conda查找包的存储库的位置**(我称之为存储库) 。在Conda的安装过程中，Continuum (Conda的开发人员)频道是默认设置的，因此，如果不进行任何进一步的修改，您的Conda将以此为默认开始搜索包。

**频道以分层顺序存在**。具有最高优先级的频道是Conda检查的第一个频道，查找您要的包。您可以更改此顺序，并向其添加频道(并设置其优先级)。

将通道 **添加到频道列表中作为的最低优先级项** 是一种很好的做法。这样，您就可以包含不属于默认设置的“特殊”包(~Continuum的频道)。因此，您最终将得到所有的缺省包，而不需要使用较低的优先级频道覆盖它们——以及您需要的“特殊”包。

![这是频道的工作方式](https://cdn-images-1.medium.com/max/1600/1*L6Va-HCq5mvifsDtjFbxlw.jpeg)


要安装在这些默认频道内无法找到的软件包，您可以在这个[网站](https://anaconda.org/anaconda/repo)上搜索 **“特殊”包**。并不是所有的包都可以在所有平台上使用(例如，操作系统和位计数，例如64位Windows)，但是，您可以将搜索范围缩小到特定的平台。如果您找到一个包含您正在寻找的包的频道，您可以将它添加到您的频道列表中。

在 **最低优先级中添加一个频道**(以实例newchannel命名):

```
conda config --append channels newchannel
```


要添加一个具有 **最高优先级** 的频道(名为newchannel)，请运行:

```
conda config --prepend channels newchannel
```

需要指出的是，在实践中，您很可能会设置最低优先级的频道。对于初学者来说，添加具有最高优先级的频道是一个边界情况。

要 **列出活动频道及其优先级**，请使用以下命令:


```
conda config --get channels
```

运行结果:

```
--add channels 'conda-forge'   # lowest priority
--add channels 'rdonnelly'
--add channels 'defaults'   # highest priority
```

还有一个方面我想总结一下。如果 **多个频道包含一个包**，而一个频道包含一个较新的版本，则频道的层次顺序决定了这两个版本中的哪一个将被安装，即使更高优先级的频道包含旧版本。

![在更高优先级通道内的版本将被安装](https://cdn-image-1.medium.com/max/1600/1*MlQ3bR4i6tYs_Jx-DEVPWg.jpeg)

### 搜索，安装和删除包

要列出当前活动环境中所有已安装的包，请运行:
```
conda list
```

该命令将列出匹配包名、版本和通道的列表:

```
# packages in environment at D:\Miniconda:
#
asn1crypto                0.22.0           py36h8e79faa_1
bleach                    1.5.0                     <pip>
ca-certificates           2017.08.26           h94faf87_0
...
wheel                     0.29.0           py36h6ce6cde_1
win_inet_pton             1.0.1            py36he67d7fd_1
wincertstore              0.2              py36h7fe50ca_0
yaml                      0.1.7            vc14hb31d195_1  [vc14]
```


**为搜索确定的包所有可以用的版本**，你可以使用搜索命令。例如，要列出```seaborn```包的所有版本(它是数据可视化的工具)，运行:

```
conda search -f seaborn
```

类似于conda listcommand，这一项将导致匹配包名、版本和通道的列表:


```
Fetching package metadata .................
seaborn           0.7.1                    py27_0  conda-forge
                  0.7.1                    py34_0  conda-forge
                  0.7.1                    py35_0  conda-forge
...
                  0.8.1            py27hab56d54_0  defaults
                  0.8.1            py35hc73483e_0  defaults
                  0.8.1            py36h9b69545_0  defaults
```

要安装一个已经位于你频道列表清单中某个频道中的包（比如 seaborn），运行如下命令（如果你不确定你想要的版本，它会自动从最高优先级的频道中找到可用的最新版本进行安装）：

```
conda install seaborn
```

您还可以 **指定包的版本**:


```
conda install seaborn=0.7.0
```

从一个频道中（比如，这个频道叫做```conda-forge```）安装一个包(例如，```yaml```，也就是YAML解析器和发射器），它 **是一个不在您的频道列表的频道内**，运行:

```
conda install -c conda-forge yaml
```

要 **更新所有已安装的包**(它只影响活动环境)，请使用以下命令:

```
conda update
```

要 **更新一个特定的包**，例如```seaborn```包，运行:

```
conda update seaborn
```


要 **删除“seaborn”包**，运行:

```
conda remove seaborn
```

在本文中，还有一个管理软件包的方面。如果您不想处理由您使用的软件包的新版本引起的兼容性问题(中断更改)，您可以 **防止该包更新**。如上所述，如果运行```conda update```命令，所有安装的包都将被更新，所以基本上是创建一个“异常列表”。怎么做呢?

### 防止包更新(锁住)

在环境的```conda-meta```目录中创建一个名为```pinned```的文件。添加您不想更新到文件的包的列表。例如，将```seaborn```包强制到0.7.x分支并将```yaml```包锁定到0.1.7版本，将以下行添加到指定的文件中:

```
seaborn 0.7.*
yaml ==0.1.7
```

### 更改环境的Python版本

您如何 **更改环境的Python版本?**。

**Python也是一个包**。为什么这与你有关？因为您将使用相同的命令替换当前已安装的Python版本，并使用另一个版本替换任何其他版本的包。

首先，您应该列出可用的Python版本:


```
conda search -f python
```


示例结果(列表包含可用的版本和通道):

```
Fetching package metadata .................
python   2.7.12     0  conda-forge
         2.7.12     1  conda-forge
         2.7.12     2  conda-forge
...
3.6.3      h3b118a2_4  defaults
         3.6.4      h6538335_0  defaults
         3.6.4      h6538335_1  defaults
```

**替换当前的Python版本**，例如，3.4.2，运行:

```
conda install python=3.4.2
```


要将Python版本 **更新到其分支的最新版本**(例如，从3.4分支更新3.4.2到3.4.5)，运行:

```
conda update python
```


### 添加PIP包

在本文开头，我建议使用Conda作为您的包和环境管理器(而不是PIP)。正如我前面提到的，**PIP包也可以安装到Conda环境中**。

因此，如果一个包在Conda通道中不可用，您可以尝试从[PyPI包索引](https://pypi.python.org/pypi)中安装它。您可以通过使用```pip``` **命令**(默认情况下Conda installer提供该命令，因此您可以在任何活动环境中应用该命令)来实现这一点。例如，如果您想安装```lightgbm```包(它是一个渐变增强框架)，运行:

```
pip install lightgbm
```


## 总结

我们来总结一下。我知道这看起来很复杂——事实上，它很复杂。然而，**利用环境会给你省很多麻烦**。

在这篇文章中，我总结了你的能力:

* 为自己选择一个合适的 **Conda安装程序**。
* 创建 **附加环境**(在根环境旁边)
* **添加或替换包**(我还解释了频道是如何工作的)
* 管理您的 **Python版本**。

在Python环境管理方面还有很多方面，所以 **请让我知道你最具挑战性的方面是什么**。如果你有一些好的实践，请告诉我，我这里没有提到。我对你的工作流程很好奇，所以如果你有什么 **建议** 的话，请在下面的响应部分分享。

## 推荐文章

如果你对这个话题感兴趣，我鼓励你也去看看这些文章。感谢这些丰富的资源[Michael Galarnyk](https://medium.com/@GalarnykMichael), [Dries Cronje](https://medium.com/@dries139), [Ryan Abernathey](https://medium.com/@rabernat), [Sanyam Bhutani](https://medium.com/@init_27), [Jason Brownlee](https://medium.com/@jason.brownlee05) 和 [Jake Vanderplas](https://github.com/jakevdp).
