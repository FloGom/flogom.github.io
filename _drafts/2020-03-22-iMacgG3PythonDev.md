---
layout: post
title: "iMac G3 Mac OS X Tiger as a development environment"
categories:
  - Old Computer
  - sustainable IT
tags:
  - imac G3
  - python
  - development environment
  - development
---

## The setup
The test setup used in this article is an iMac G3 DV 400MHz, under Mac OS X Tiger (10.4.11).

## The goal
The goal is to set up a python development environment. The main objective is breakdown in several steps:
1. Setting-up basic python installation (with IDLE to begin)
2. Install library like numpy, matplotlib, scipy...
3. Add package management with `brew`

Let's brew it!

![brew logo](/assets/2020-03-22-img/homebrew-256x256.png)

## 1. Basic Python install
The Mac OS comes with a standard python install, in that case it's *Python 2.3.5*... yeah! Quiet old already at the time of the writing.

And this python install comes with no IDE.

If Xcode is installed, then a nice IDE waits for you.


## 3. Package management
### First try with Xcode v2.2.1
The package management is done by Tigerbrew from [mistydemeo](https://github.com/mistydemeo/tigerbrew).

After the installation, the `brew doctor`command throws out some warnings (after a very long computation time... be patient.. it's 400MHz after all), nothing to worry about. Hints are given by the program to solve them. One warning say Xcode path are not set properly, but the provided hint does not help since `xcode-select` command does not exist. And trying to install the new version of *curl* with  `brew install curl`, the C compiler is missing, and `pkgutil` also. Xcode tools might be a little old.

Since Xcode v2.2 (shipped version in the Mac OS X install DVD) does not ship Command Line Tools (CLT). A newer version of the software needs to be installed. The version 2.5 comes with CLT.

### Second try with Xcode v2.5
After Xcode installation and restart, the command `brew doctor` threw out less warnings. The CLT are available!

The command `brew install git`

It built successfully xz in  14.2 min
Then failed downloading gnu-tar, due to bad OpenSSL connection

Let's try fetching curl first with `brew install curl`

## 4. Storing the package for futur installation
Keeping all those precious packages will help in the futur.
Everything downloaded is stored in `~/Library/Caches/Homebrew`.

If the package is in this directory, the following command will 
install that specific package (here : `wget-1.14.tar.gz`):
`brew install -f wget-1.14.tar.gz`

## making bootles to keep the base update
It's possible to bottle a package once it has been compile. It's like making a binary.
I must consider bottling all the packages not already bottled for G3 ppc, to save times for the next install.
Reach the github of tiger brew

## links
[mg Xcode tools](https://macintoshgarden.org/apps/apple-xcode)