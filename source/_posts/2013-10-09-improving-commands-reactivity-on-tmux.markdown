---
layout: post
title: "Improving commands reactivity on Tmux"
date: 2013-10-09 18:13
comments: true
<!-- published: false -->
tags: [ tmux, configuration, UX ]
categories: [ tmux, configuration, UX ]
---

I'm going to describe how you can improve the reactivity of your `tmux` commands. All configuration should be added to your `~/.tmux.conf`.
<!--more-->
## Speed up command sequence

By default, there is a latency time when hitting the <kbd>PREFIX</kbd> because `tmux` is [waiting for an escape sequence](http://mutelight.org/practical-tmux):

> `escape-time time`
>
> Set the time in milliseconds for which tmux waits after an escape is
> input to determine if it is part of a function or meta key sequences.
> The default is 500 milliseconds.

So just set this value [below cognitive perceivable threshold (`~200ms`)](http://stackoverflow.com/questions/536300/what-is-the-shortest-perceivable-application-response-delay) :
```bash
# Faster Command Sequences (don't wait for esc/meta-key sequence): 
set -s escape-time 100
```

