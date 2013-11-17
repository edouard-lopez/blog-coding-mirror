---
layout: post
title: "Installing and using tmux on Linux Mint (Ubuntu)"
date: 2013-10-03 17:45
comments: true
tags: [ tmux, shell, productivity, how-to ]
categories: [ tmux, shell, productivity, how-to ]
---
## What can it do for you?
* You can <strong>detach a session and later attach it back</strong> to finish what you started (think remote/SSH here).
* You can work with others people on the same document, this is also called <em>peer programming/editing</em> :
<!--more-->
## Install
```bash
apt-get install tmux
```

## Usage
To create a termine, type in a terminal:
```bash
tmux
```
Now you're in a ``tmux`` session.

## Video
I write this article after watching the [video tmux Quick Start by Sam Livingston-Gray.](https://www.youtube.com/watch?v=wKEGA8oEWXw)
<iframe width="420" height="315" src="//www.youtube-nocookie.com/embed/wKEGA8oEWXw?rel=0" frameborder="0" allowfullscreen></iframe>

## References

1. [screen and tmux daily cheatsheet](http://www.dayid.org/os/notes/tm.html)
2. [tmux shortcuts & cheatsheet](https://gist.github.com/MohamedAlaa/2961058)
3. [Great config by @jasonwryan](https://bitbucket.org/jasonwryan/centurion/src/2c63835765d143fe36cfa0c077882dfecc3267d7/.tmux/conf?at=default)

