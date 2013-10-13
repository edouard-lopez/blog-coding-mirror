---
layout: post
title: #Home and End keys not working with vim in tmux#
date: 2013-10-04 09:35
comments: true
categories: [tmux, vim, solved]
---

So the other day I [installed `tmux`](install-and-using-tmux-on-linux-mint-ubuntu) and when working in `vim` I noticed that <kbd>Home</kbd> and <kbd>End</kbd> keys stopped working.
<!--more-->
## Why?
If you set your `tmux` to use `screen-256color` it will break the <kbd>Home</kbd> and <kbd>End</kbd> keys behavoir (to jump to the beginning/end of a line).

## Solution
Simply [force mapping of both keys in vim](http://stackoverflow.com/a/9453541/802365) by editing your `~/.vimrc` as follow:

```bash
    ##############
    # tmux fixes #
    ##############
    # Handle tmux $TERM quirks in vim
    if $TERM =~ '^screen-256color'
        map <Esc>OH <Home>
        map! <Esc>OH <Home>
        map <Esc>OF <End>
        map! <Esc>OF <End>
    endif
```

Don't forget to close and re-open your `vim`.
