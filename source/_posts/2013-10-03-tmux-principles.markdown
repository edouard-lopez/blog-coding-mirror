---
layout: post
title: "Tmux principles"
date: 2013-10-03 16:30
comments: true
tags: [ tmux, productivity, concept ]
categories: [ tmux, productivity, concept ]
---
Tmux is a multiplexer, which means you can [manage several virtual terminals in one windows](https://en.wikipedia.org/wiki/Tmux).
<!--more-->
## Client and Server
Tmux works with **two distinct processes**, one is going to be a client and the other a server – running in the background, _i.e._ a daemon. Different processes means, you can kill the client while the server will stay alive.

This mechanism is what support detach/attach feature.

## Attach/Detach
How is this useful? Imagine you start a ``tmux`` session on a remote machine:

1. you start some _work_ ;
2. _detach_ from the ``tmux``'s session and logout from the server ;
3. at home, you go back to the server and _re-attach_ the ``tmux``'s session.

Then all your context is still running. So now you can start some script without worrying to logout, you just have to **detach and re-attach** to have a peek in.

## <kdb>prefix</kdb> for keyboard control
The <kbd>prefix</kbd> is a keys combination, default is <kbd>Ctrl</kbd>+<kbd>b</kbd>, that tell ``tmux`` to treat the following key as an internal action. So it basically create a namespace to distinguishes between what should be send directly to the terminal (default) and what should be manage by ``tmux`` (_e.g._ detaching with <kbd>prefix</kbd>+<kbd>d</kbd>).

If you're looking for the list of default key-binding, simply type <kbd>prefix</kbd>+<kbd>?</kbd> in a ``tmux`` session.
Here a two essential bindings:

* <kbd>prefix</kbd>+<kbd>d</kbd>: detach from current session ;
* <kbd>prefix</kbd>+<kbd>c</kbd>: create new ``tmux`` window


## Scrolling & copying
Tmux [break the native scrolling behaviour](http://youtu.be/wKEGA8oEWXw?t=4m55s) so you've to activate a special mode to scroll your session. This mode is called the *copy mode* and you enable it with <kbd>prefix</kbd>+<kbd>[</kbd> (you can bind it something else than square bracket).

## Session, Windows and Panes
Evan Travers give a pretty good definition of those concept in its article [Workflow in Tmux:](https://coderwall.com/p/_g2vpq)

<blockquote>Sessions are groups of windows, and a window is a layout of panes</blockquote>

* <kbd>→</kbd> or <kbd>←</kbd>: navigation through panes ;
* <kbd>x</kbd>: closing a pane ; you can also use <kbd>Ctrl</kbd>+<kbd>d</kbd>, which is probably more familiar and doesn't ask for confirmation.

## References

* [tmux Tutorial - Split Terminal Windows Easily](http://lukaszwrobel.pl/blog/tmux-tutorial-split-terminal-windows-easily)
