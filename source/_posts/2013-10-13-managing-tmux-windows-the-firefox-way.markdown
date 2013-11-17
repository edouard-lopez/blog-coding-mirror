---
layout: post
title: "Managing Tmux' windows the Firefox way"
date: 2013-10-13 19:22
comments: true
tags: [ tmux, configuration, productivity ]
categories: [ tmux, configuration, productivity ]
---

When switching to `tmux` I found the default configuration to manage and navigate among windows quite annoying. Even more considering I had to press the <kbd>PREFIX</kbd> key with yet further shortcuts to do the same old thing (open/switch tabs). So here I explain how to:

1. bind a shortcut directly (no more <kbd>PREFIX</kbd> :) ;
2. set <kbd>Ctrl</kbd>+<kbd>t</kbd> to open windows/tab ;
2. set <kbd>Ctrl</kbd>+<kbd>PageUp</kbd> and <kbd>Ctrl</kbd>+<kbd>PageDown</kbd> to switch to previous/next tab ;
<!--more-->

## Binding Keys Directly

Before I go further, and as most of you already know ([<abbr title="Read The Fucking Manual">RTFM</abbr> of `tmux`](http://www.openbsd.org/cgi-bin/man.cgi?query=tmux))… The `-n` flag used with `bind-key` allows to bind a key directly (_i.e._ without requiring to press <kbd>PREFIX</kbd>):

> if -n is specified, it is not necessary to use the prefix key, command 
> is bound to key alone

## Opening and switching Tabs

I like to have consistent behaviors between my applications. So below is the `tmux` configuration to have the same shortcuts –to open and navigate tabs– as the one in `Firefox`. Edit your `~/.tmux.conf` to add the binding.

```bash 
# Configuration to open new tab with <kbd>Ctrl</kbd>+<kbd>t</kbd>
# Ctrl-t opens new tab (window)
bind-key -n C-t new-window
```

```bash 
# Configuration to switch tabs with <kbd>Ctrl</kbd>+<kbd>PageUp</kbd> and <kbd>Ctrl</kbd>+<kbd>PageDown</kbd>
# PageUp to switch to previous tab
bind-key -n C-PPage previous-window
# PageDown to switch to next tab
bind-key -n C-NPage next-window
```

If you want to go further, there is plenty of [others `Firefox` shortcuts](https://support.mozilla.org/en-US/kb/keyboard-shortcuts-perform-firefox-tasks-quickly?redirectlocale=en-US&redirectslug=Keyboard+shortcuts#w_windows-tabs) to configure.

## References

* [.tmux.conf](https://github.com/sickill/dotfiles/blob/master/.tmux.conf) by [sickill](https://github.com/sickill)
