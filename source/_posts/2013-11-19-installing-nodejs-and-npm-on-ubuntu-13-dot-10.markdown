---
layout: post
title: "Installing Nodejs and NPM on Ubuntu-13.10"
date: 2013-11-19 17:24
comments: true
tags: [ install, nodejs, npm, ubuntu, ubuntu-13.10 ]
categories: [ install, nodejs, npm, ubuntu, ubuntu-13.10 ]
---

Actually `nodejs` and `npm` have **merged into the `nodejs`** package.

The best way to install, which is also the easiest, it is by using [Chris Lea PPA.](https://launchpad.net/~chris-lea/+archive/node.js) The [offical github repository is even recommending this approach](https://github.com/joyent/node/wiki/Installing-Node.js-via-package-manager#ubuntu-mint-elementary-os) :

```bash
sudo apt-get update
sudo apt-get install -y python-software-properties python g++ make
sudo add-apt-repository -y ppa:chris-lea/node.js
```

```bash
sudo apt-get update
sudo apt-get install nodejs
```
**Done!**

## What about the symlink ?

Well, you *don't need to create it anymore*, the symlink to `/usr/bin/nodejs` is managed by the package. You can **verify your installation** with :
```bash
nodejs -v
# v0.10.*
npm -v
# 1.3.*
```
