---
layout: page
title: Software
---

All software required for courses is open source and free unless otherwise noted.
If you have any questions or problems regarding software installation, please contact
your instructor.


### Git and GitHub

Git is version control software, which helps you keep track of changes made to files.
GitHub is a repository for data and code tracked with Git, and is a mechanism for publishing
and collaborating on project development.

#### GitHub Desktop App for Windows, macOS

* If you do not already have one, please register for a [GitHub](https://github.com) account.
Please note that your name and email will be publicly visible through GitHub by default,
but more information on controlling privacy settings can be found
[here](https://help.github.com/articles/setting-your-commit-email-address-on-github/).
* The website for [GitHub Desktop](https://desktop.github.com) should auto-detect your operating system
and allow you to download and install the software.
* We recommend installing [Atom](https://atom.io) if you do not already have a preferred text editor;
this website will also auto-detect your operating system.

#### Command line tools for Windows (only for optional third week)

If you would like to work with Git on the command line in the third week of class on a Windows laptop,
also install [Git for Windows](https://gitforwindows.org). Please note that this also installs Git Gui,
which we will not use.

#### Command line tools for macOS (only for optional third week)

If you would like to work with Git on the command line in the third week of class on a Mac laptop,
you will also need to install command line Git tools by clicking on "GitHub Desktop" in the top menu of the app,
then selecting "Install Command Line Tool." You will then be able to access the software through
Terminal, which you can locate by clicking on your Desktop, selecting "Go" in the menu at the top,
and clicking on "Utilities."


### Python

We will be using Python version 3 (and above) for our courses,
as well as the following packages:
[pandas](http://pandas.pydata.org), [jupyter notebook](http://jupyter.org),
[numpy](http://www.numpy.org), [matplotlib](https://matplotlib.org),
and [plotnine](https://plotnine.readthedocs.io/en/stable/).
We recommend installing Python using Anaconda,
which includes most of the packages listed above:
* Download the [Anaconda](https://www.anaconda.com/download/) installer for
Python 3.x for your particular operating system
* Double-click the downloaded file and follow the prompts to install Anaconda

Following installation, open the following command line software based
on your operating system to install the final package:
* MacOSX: Terminal, locate by clicking on your Desktop, selecting "Go" in the menu at the top,
and clicking on "Utilities"
* Windows: Anaconda Prompt
* Both MacOSX and Windows: copy and paste the following code onto the
command line and execute by hitting "Enter":
`conda install -c conda-forge plotnine`


### R and RStudio

R and RStudio are separate downloads.
R is the "engine", while RStudio is an integrated desktop environment (IDE) that makes using R much more pleasant.
R must be installed before RStudio.
Follow the instructions below for your operating system to install them.
If you are working on a computer owned by Fred Hutch,
it may also be possible to install these programs through the self-service app.

#### Windows

* Download the installer for the latest version of R from [CRAN](http://cran.r-project.org/bin/windows/base/release.htm).
  The file will begin downloading automatically.
* Double-click the downloaded `.exe` file and follow the prompts to install.
* Go to the [RStudio download page](https://www.rstudio.com/products/rstudio/download/#download).
* Under _Installers_, click the link for the _Windows Vista/7/8/10_ installer to download it.
* Double-click the downloaded `.exe` file and follow the prompts to install.
* Once both are installed, launch RStudio and make sure there are no error messages.

#### macOS

* Download the installer for the latest version of R compatible with your version of macOS from [CRAN](https://cran.r-project.org/bin/macosx/).
  If you are not using a recent version of macOS you may have to scroll down to _Binaries for legacy OS X systems_ and find the one appropriate for your version of macOS.
  To check what version of macOS you are using, click the apple icon in the upper left corner of your screen and go to _About This Mac_.
* Double-click the downloaded `.pkg` file and follow the prompts to install.
* Download the installer for [XQuartz](https://www.xquartz.org/).
* Double-click the downloaded `.dmg` file, then open the XQuartz folder that appears on your desktop. Double-click the `.pkg` file and follow the prompts to install.
* Go the the [RStudio download page](https://www.rstudio.com/products/rstudio/download/#download).
* Under _Installers_, click the link for the _Mac OS X 10.6+ (64-bit)_ installer to download it.
* Double-click the downloaded `.dmg` file, then open the RStudio folder that appears on your desktop. Drag the RStudio icon into the Applications folder.
* Once everything is installed, launch RStudio and make sure there are no error messages.