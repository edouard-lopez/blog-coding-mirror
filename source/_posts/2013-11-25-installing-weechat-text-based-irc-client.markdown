---
layout: post
title: "Installing Weechat: text-based IRC Client"
date: 2013-11-25 12:46
comments: true
tags: [ IRC, weechat, install, ubuntu ]
categories: [ IRC, weechat, install, ubuntu ]
published: true
---

`WeeChat` is an IRC client with a text-based user interface. It is designed to be **light, fast and extensible** with plugins (<abbr title="also known as">aka</abbr> scripts).

Since its first release in 2003, an [Android client](https://github.com/ubergeek42/weechat-android), a [QT interface](http://www.weechat.org/download/devel/) as well as [web](http://weecloud.jit.su/) and [Emacs](https://github.com/the-kenny/weechat.el) have been developed.
<!--more-->
[![Weechat default appareance](/images/screenshots/weechat-default.png)](/images/screenshots/weechat-default.png)

## Features

WeeChat as [plenty of features](http://www.weechat.org/about/features/) and particularly :

* Cross-platform support ([`Android`](https://github.com/ubergeek42/weechat-android), `Linux`, `UNIX`, `MacOS`, `Windows`, etc.) ;
* `IPv6`, `SSL` and proxy connections ;
* Spell checker (using `aspell`) ;
* Scripting support for many languages (`Perl`, `Python`, `Ruby`, `Lua`, `Tcl`, etc.) ;
* Screen splitting ;
* Dynamic filtering of lines ;
*  and more.

## Installation

The package is in the official repositories. However, there is a [stable weechat PPA](https://launchpad.net/~nesthib/+archive/weechat-stable) maintained by a [`nesthib`](https://launchpad.net/~nesthib):
```bash
sudo add-apt-repository ppa:nesthib/weechat
sudo apt-get update
sudo apt-get install weechat
# run
weechat
```

Now you can start [customizing your settings](http://weechat.org/files/doc/stable/weechat_user.en.html#screen_layout) and [install some plugins](/useful-plugins-for-weechat-users).
