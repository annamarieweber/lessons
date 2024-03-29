---
title: Setup
---

# Setup
Participation in the MSSE Bootcamp will require use of your own personal computer or laptop and installation of some software.

> ## Windows users take note
>
> If you are working on a Windows computer, participation in the course will require you to install the Windows Subsystem for Linux (WSL).
> You should install WSL 2, you will need to have the Windows 10 OS with the following version requirements:
> 
> * For x64 systems: Version 1903 or higher, with Build 18362 or higher.
> * For ARM64 systems: Version 2004 or higher, with Build 19041 or higher.  
> 
> If you haven't updated your computer in a while, these updates could take a considerable amount of time. 
> Plan accordingly!
{: .prereq}

Please follow the instructions given here to make sure you have the necessary software installed. We will be using Python and the conda package manager from Anaconda. If you are on MacOS or Linux and you already have Anaconda (or miniconda) installed, skip to the compilers portion of these set-up instructions. If you do not have Anaconda or miniconda installed please see the appropriate section below.

First see the appropriate section in the section [Operating System Specific Instructions](#operating-system-specific-installation-instructions), then everyone should do the portion in [Installation Instructions for Everyone](#installation-instructions-for-everyone).

> ## Anaconda vs. Miniconda
> Anaconda is a distribution of Python, the conda package manager, and several third-party libraries which are commonly used in data science.
> Miniconda contains only Python and the conda package manager. You will be able to install any package you would like later using miniconda. 
> Miniconda will take up a lot less space on your computer.
> We will be learning to manage conda environments and install the packages we need, so we consider miniconda to be the better option between the two.
> If you already have Anaconda installed, however, there is no need to install miniconda.
{: .callout}

## Operating System Specific Installation Instructions
Pick the appropriate operating system and follow these instuctions
1. [MacOS miniconda and compiler installation](#mac-os)
1. [Linux miniconda and compiler installation](#linux)
1. [Windows miniconda and compiler installation](#windows)

## Installation Instructions for Everyone
1. [Creating a conda environment - ALL USERS](#creating-a-conda-environment)
1. [Setting up and configuring git - ALL USERS](#installing-and-configuring-git)
1. [Making a GitHub Account and setting up an SSH key - ALL USERS](#github)
1. [Installing a text editor - ALL USERS](#text-editor)

## Mac OS

### Miniconda Installation
You can download and run the installer at this [link](https://docs.conda.io/en/latest/miniconda.html).

### Compilers
MacOS users should [install XCode](https://developer.apple.com/xcode/). An easy way to install XCode is through the [Mac App Store](https://apps.apple.com/us/app/xcode/id497799835?mt=12).

After installing XCode, proceed to the next section [Creating a MSSE Bootcamp conda environment](#creating-a-conda-environment).

## Linux

### Miniconda Installation
You can download and run the installer at this [link](https://docs.conda.io/en/latest/miniconda.html).

### Compilers
After installing miniconda, you will need to install compilers for the C++ section of the course. Use this command to install compilers
~~~
sudo apt install build-essential
~~~
{: .language-bash}

After this command has completed, proceed to the next section [Creating a MSSE Bootcamp conda environment](#creating-a-msse-bootcamp-conda-environment).

## Windows
If your computer uses the Windows operating system, we require installing Windows Subsystem for Linux (WSL). Follow the installation instructions at [this link](https://docs.microsoft.com/en-us/windows/wsl/install-win10). If you don’t have a preference on Linux distribution, we recommend installing Ubuntu 20.04. 

Once WSL is installed, open your ‘Start’ menu and choose ‘Ubuntu’. This should open a terminal window. The first time you have opened Ubuntu, you may see a message which says “Installing, this may take a few minutes…”. After the installation is done, you will have to create a username and password. After these are created, you should be able to use the terminal.

The Windows Subsystem for Linux is like running another computer inside your computer. It is a different operating system and has different software installed than your Windows computer. For the WSL, you have to install miniconda from the terminal in your Linux operating system. Note that if you if you are using the WSL, your Linux OS is completely separated from your Windows operating system. This means that software installed on one operating system is not available in the other.

### WSL Miniconda Installation
You are now using a Linux OS under Windows. You must install miniconda from the command line. From your terminal execute the following lines:  
~~~
wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh
bash Miniconda3-latest-Linux-x86_64.sh
~~~
{: .language-bash}

After installation, close and reopen your terminal window. If you do not see (base) before your username on the command line, type

~~~
conda init
~~~
{: .language-bash}

### Compilers
After installing miniconda, you will need to install compilers for the C++ section of the course. Use this command to install compilers
~~~
sudo apt install build-essential
~~~
{: .language-bash}

After this command has completed, proceed to the next section [Creating a MSSE Bootcamp conda environment](#creating-a-msse-bootcamp-conda-environment).


# Creating a conda environment
Everyone should complete and read this section after installing miniconda.

To make a great deal of compilation and installation simpler we will create a conda environment. Environments isolate software from this project from the rest of the dependencies on your laptop.

After installing miniconda, type the following command into your terminal. This creates an environment called “msse-python” which runs Python 3.9.


~~~
conda create -n msse-python python=3.9
~~~
{: .language-bash}

After creating the environment, activate it using the command

~~~
conda activate msse-python
~~~
{: .language-bash}

Next, install the Python libraries jupyter and matplotlib

~~~
conda install matplotlib
conda install -c conda-forge notebook
~~~
{: .language-bash}

You now have a new environment `msse-python` created which has the Python Standard Library, matplotlib, and jupyter installed. This is the environment we will be using for our initial coding projects.

To deactivate the environment, use

~~~
conda deactivate
~~~
{: .language-bash}


## Installing and configuring git

### Installation
We will be using the `git` software for version control during this course. This portion walks you through installing and configuring `git`.

If you do not have the environment activated, activate it first:

~~~
conda activate msse-python
~~~
{: .language-bash}

Next, make sure you have git installed.

You can check if git is installed using the following command in your terminal:

~~~
git --version
~~~
{: .bash}

Make sure that this outputs at least version 2.28. If you do not have git installed, or if it is an older version of git, 
you can install git using conda:

~~~
conda install -c conda-forge git
~~~
{: .language-bash}

### Configuring Git

The first time you use Git on a particular computer, you need to configure some things.

First, you should set your identity.
One of the most important things that version control like Git does is to keep track of who changes what.
This helps repository maintainers coordinate the efforts of all the people who contribute to the project.
Most importantly, it makes it easier to figure out who to blame when something goes wrong.
You can provide git your name and contact information with the following commands:

> ## Configuring git
> In the command below, you do not need to put your name or your email address in all caps.
{: .callout}

~~~
git config --global user.name "YOUR_FIRSTNAME YOUR_LASTNAME"
git config --global user.email "YOUR_EMAIL_ADDRESS"
~~~
{: .bash}

Next, you will need to set the name of the default branch git uses.
We will discuss in more detail during the bootcamp.
The following command will set your default branch name to be "main"

~~~
git config --global init.defaultBranch main
~~~
{: .bash}

Next, you might want to change the Git text editor.
As we will see later, certain Git commands will open text files.
When this happens, Git will use your environment's default text editor, which might not be the editor you are most comfortable using.
Using configuration commands, you can tell Git to use your favorite editor.

Everyone can use Vim as a text editor, but you can set it to your preference. **If you are using the WSL, use Vim as your text editor**:

~~~
$ git config --global core.editor "vim"
~~~
{: .bash}

A more complete list of possible editors is available [here](http://swcarpentry.github.io/git-novice/02-setup/index.html).

You can check the configuration commands that you have set using:

~~~
$ git config --list
~~~
{: .bash}

## GitHub

If you do not yet have a GitHub account, you will need to create one.
To create an account, navigate to [github.com](https://github.com/), and click "Sign up". 
When creating your GitHub username, remember that this is a professional profile where you can showcase your work.
Keeping this in mind, make sure that your GitHub username is both **professional** and **recognizable**.

### GitHub Credentials
We will be using the command line interface for GitHub. 
GitHub *very recently* deprecated using a username and password from the command line.
Instead, you will need to create something called an ssh key to verify your account.

Follow the [instructions given by GitHub](https://docs.github.com/en/github/authenticating-to-github/connecting-to-github-with-ssh) to create an SSH key and add it to your account.

## Text Editor
Everyone should have a text editor they can use to edit Python. If you do not have a preference for text editors, we recommend [Visual Studio Code](https://code.visualstudio.com/). If you are using WSL, see [these instructions](https://code.visualstudio.com/docs/remote/wsl) for installing Visual Studio Code for use with WSL.





