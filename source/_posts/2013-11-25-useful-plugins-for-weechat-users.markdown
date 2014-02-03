---
layout: post
title: "Useful plugins for Weechat users"
date: 2013-11-25 15:16
comments: true
tags: [ IRC, weechat, tips, configuration, install ]
categories: [ IRC, weechat, tip, configuration, install ]
published: false
---

/script load auto_away.py autoconnect.py buffers.pl go.py menu.pl spell_correction.py spell_menu.pl weeget.py

So we already saw how to install Weechat, here are some scripts I found interesting to share with you.
<http://weechat.org/scripts/source/stable/buffers.pl.html/>

/script load buffers.pl **autoconnect.py auto_away.py go.py**

### Useful scripts

* **buffers.pl**: Sidebar with list of buffers with mouse support (not in ``tmux`` ?) ;
* anotify.py: Notifications of private messages, highlights, DCC send/receive and more. (requires: libnotify)
* **autoconnect.py**: Reopen servers and channels opened last time WeeChat closed. 
* **auto_away.py**: A simple auto-away script. 

    /autoaway 10 'Wandering somewhere else'
    /save


* bandwidth.py: Displays network interface bandwidth on a bar. 
* ?**buddylist.pl**: A simple buddylist to show if your buddies are online/away/offline. 
* ?**chanstat.py**: Displays channel's peak, low and average users. 
* coords.pl: Select text, nicks or URLs on screen with mouse or keyboard.
* **+go.py**: Quick jump to buffers.

    /key bind meta-g /go
    # then use Alt-G to activte


* inotify.py: Notification script using libnotify or dbus with screen support. (requires: inotify-daemon) 
* **menu.pl**: Bar with popup menu.

    /key bind meta-m /menu
    # then use Alt-M to activte


* multiline.pl: Multi-line edit box, also supports editing of multi-line pastes. 
* ? **pyrnotify.py**: Send notifications to remote client using ssh and libnotify. (requires: libnotify) 
* rnotify.tcl: Sends highlights to (remote) client using libnotify. (requires: libnotify) 
* screen_away.py: Set away status when detaching and attaching from screen or tmux. 
* **+spell_correction.py**: Correction for misspelled words in command line. 

    /aspell listdict
    /aspell setdict fr
    /aspell enable
    /save


* #spell_menu.pl: Popup menu to choose spell checker corrections. (requires: menu.pl) 
* sshnotify.py: A notify script which uses ssh. (requires: notify-send) 
* unset_unused.pl: Remove options of scripts that are no longer installed. 
* **~urlbar.py**: Display a url bar for easy clicking or selecting. 
* weetweet.py: WeeChat twitter client. (requires: python twitter lib >= 1.9.4, python3 (outside WeeChat))
* #**whatismyip.py**: Display external ip address. 
* #**xfer_setip.py** : Set xfer own ip with external ip. 




