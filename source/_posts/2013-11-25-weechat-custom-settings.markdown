---
layout: post
title: "Weechat Custom Settings"
date: 2013-11-25 14:26
comments: true
tags: [ IRC, weechat, tips ]
categories: [ IRC, weechat, tips ]
published: true
---

After an `upgrade` I lost all my `weechat` configurations, so here is a quick start to get the follow results.

[![Weechat final customization](/images/screenshots/weechat-final-customization.png)](/images/screenshots/weechat-final-customization.png)

<!--more-->

## Freenode
I'm going to [connect to `Freenode` using SSL](http://www.weechat.org/files/doc/weechat_faq.en.html#irc_ssl_freenode).
<!--more-->

## Certificates
First we define the file with certificates:
```bash
/set weechat.network.gnutls_ca_file "/etc/ssl/certs/ca-certificates.crt"
```
Then set our configurations:
```bash
# Server configiguration
/server add freenode cameron.freenode.net -port 7000
/set irc.server.freenode.addresses "cameron.freenode.net/7000
/set irc.server.freenode.ssl on
/set irc.server.freenode.ssl_dhkey_size 1024

# re/auto/connect
/set irc.server.freenode.autojoin "#giroll, #labx, #leloop, #bash, #awk"
/set irc.server.freenode.autoconnect on
/set irc.server.freenode.autoreconnect on

# username
/set irc.server.freenode.nicks "ed8, ed[8], edoz"
/set irc.server.freenode.username "ed8"
/set irc.server.freenode.realname "Édouard Lopez"
/set irc.server.freenode.away_check 15
```
Why using `cameron.freenode.net` ? Cause it support [`SSL` and is located in Lithuania](http://freenode.net/irc_servers.shtml).

## Mozilla
Here I won't be using `SSL`, so it's a bit simpler. Also I duplicate settings for this server:
```bash
/server add mozilla irc.mozilla.org -port 6667 -auto
/set irc.server.mozilla.autojoin "#firefox, #l10n, #webtools "

# re/auto/connect
/set irc.server.mozilla.autojoin "#giroll, #labx, #leloop, #bash, #awk"
/set irc.server.mozilla.autoconnect on
/set irc.server.mozilla.autoreconnect on

# username
/set irc.server.mozilla.nicks "ed8, ed[8], edoz"
/set irc.server.mozilla.username "ed8"
/set irc.server.mozilla.realname "Édouard Lopez"

/set irc.server.mozilla.away_check 15
```

# Interface Tweaks

Activate logging, set up the UI:
```bash
/set logger.file.auto_log on
/window splith

# Layout
/set weechat.look.buffer_time_format "%H:%M"
/set weechat.look.separator_horizontal "~"
/set weechat.bar.nicklist.position right
/layout save

# Nick
/set weechat.color.chat_time gray
/set weechat.bar.status.color_bg gray
/set weechat.color.chat_nick_self *!lightgreen
/set buffers.color.current_bg cyan
/set buffers.color.number black
/set buffers.color.hotlist_message_bg green
/set buffers.color.hotlist_message_fg white

# status bar
/set weechat.bar.status.hidden off
/set weechat.bar.status.color_bg darkgray
/set weechat.bar.status.items "buffer_number+:+buffer_name+{buffer_nicklist_count}+buffer_filter,completion,scroll"
```

## Alias
```bash
/alias split /window splith
/alias id /msg NickServ IDENTIFY <CHANGE_ME>
```

Connect and save settings:
```bash
/script autoload
/connect -all
/save
```

I'm going to address [weechat scripts/plugins in a following ticket](/useful-plugins-for-weechat-users) as its can be quite long to explain.

## Read more

* [WeeChat User’s Guide](http://weechat.org/files/doc/devel/weechat_user.en.html)
* **{fr}** [Weechat, installation, configuration et utilisation](http://doc.fedora-fr.org/wiki/Weechat,_installation,_configuration_et_utilisation)
