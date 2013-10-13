---
layout: post
title: "Tmux solving word splitting"
date: 2013-10-09 18:13
comments: true
<!-- published: false -->
categories: [ tmux, configuration, solved, UX ]
---

I'm going to provide some way to tweak the reactivity of your `tmux`, and so each config should be added to your `~/.tmux.conf`.
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

## Directly binding keys (no <kbd>PREFIX</kbd>)

Before I go further, and as most of you already know ([<abbr title="Read The Fucking Manual">RTFM</abbr> `tmux`](http://www.openbsd.org/cgi-bin/man.cgi?query=tmux))… You should know the role of the `-n` flag when used with `bind-key`:

> if -n is specified, it is not necessary to use the prefix key, command 
> is bound to key alone

## Opening and switching Tabs

I like to have consistent consistent behaviors between my applications. So below is the configuration for `tmux` to have shortcuts to open and navigate tabs same as the one in `Firefox`.

* New tab shortcut:
```bash
# Ctrl-t opens new tab (window)
bind-key -n C-t new-window
```

* Switching tab shortcut:
```bash
# Page Up/Down move to previous/next tab (window)
bind-key -n C-PPage previous-window
bind-key -n C-NPage next-window
```

## References

* [.tmux.conf](https://github.com/sickill/dotfiles/blob/master/.tmux.conf) by [sickill](https://github.com/sickill)
