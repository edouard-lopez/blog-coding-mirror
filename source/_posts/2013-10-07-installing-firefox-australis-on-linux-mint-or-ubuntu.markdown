---
layout: post
title: "Installing Firefox Australis on Linux Mint or Ubuntu"
date: 2013-10-07 11:30
comments: true
published: true
categories: [UX, Firefox]
---

I'm a long time Firefox user, and I'm happy to see it being at the lead of web technology again. So when the [news about Australis](https://twitter.com/MozillaUX/status/386418196473217024) – the upcoming desktop Firefox design refresh – came from the [MozSummit](https://wiki.mozilla.org/Summit2013) I went to get my hands on it and have a ride.
<!--more-->
So _Australis_ idea to to redesign the [_Tab Strip_ UI](https://wiki.mozilla.org/Tab_Strip_Visual_Redesign).

{% img left http://getaustralis.com/images/image-mainWindow.png 'Firefox Australis, new UX' %}

## Installing Process is Crucial

Installing should be straight-forward as its the **first barrier for your users** to use your product. In the case of `Australis`'s website, the **design is impeding the installation task**.

Indeed, the only versions available here are the `x86`/`32bits`. So what happen if you are running on a `x86_64`/`64bits` platform? Well you're in a dead-end… 

Except if you know how this things work, which means [hitting directly the directory holding the files](https://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-ux/).

### Installation for `x86` Architecture

Simply go to the official [Australis](http://gtaustralis.com/) website, download, extract and run the Linux archive.

### Installation for `x86_64` Architecture

If you try to download the `tar.bz2` using the link on the main page, you'll get the `x86` version. Hence running `./firefox` will throw the following error:
```bash
./firefox: error while loading shared libraries: libstdc++.so.6: cannot open shared object file: No such file or directory
```

So indeed, go to the [branch directory to find the `x86_64` version](https://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-ux/) or run this:
```bash
wget https://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-ux/firefox-27.0a1.en-US.linux-x86_64.tar.bz2
tar xvjf ./firefox-*.linux-x86_64.tar.bz2
cd firefox/
./firefox &
```
And boom! You got the new `Australis` UX.

## Platform Sniffing and Dead-end

When trying to download a piece of software directly from the editor website, many try to sniff your platform and web browser to provide the right version of there app. For instance, [LastPass](https://lastpass.com/misc_download.php) do that (correctly) :

{% img left /images/screenshots/lastpass-sniffing-platform-and-browser.png 'Platform and browser sniffing on LastPass download page' %}

Be aware that this this kind of detection can **sometimes come in the way** of the user instead of helping him. For instance, I'm French but use a browser with English locale and sometimes I prefer to have content in French. So at least provide of way to switch from one setting to another.

LastPass implementation is nice, as they provide a recommended download, based on their detection, but still **give the possibility** to switch to a different option. 

So don't assume to much on what users are going to do as it can backfire.


