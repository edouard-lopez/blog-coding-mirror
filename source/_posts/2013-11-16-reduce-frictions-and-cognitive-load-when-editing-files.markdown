---
layout: post
title: "Reduce Frictions and Cognitive Load When Editing Files"
date: 2013-11-16 23:34
comments: true
tags: [ shell, productivity, vim, UX ]
categories: [ shell, productivity, vim, UX ]
---

As a Linux/Mac user you have already edited file using the command line editor (_e.g._ `vim`, `nano`, `emacs`, etc.). And **you repeat this** tens to hundreds times a day. So what the problem ? 

When you attempt to complete this task, your goal to is clear (**_edit_ a file**), but the way to it is full of traps :

1. do you have enough privileges ? → cognitive load
2. did you do any typing error invoking the command ? → friction
3. do you have your preferred editor installed on this machine ? → cognitive load

## Wät ?

Understanding all this and the [KISS principle](http://en.wikipedia.org/wiki/KISS_principle), I give you the _shortest command to **e**dit a file_:

    e /path/to/file   # simplify file editing

Being one-character long come with the additional benefices of:

* **super-easy to remember**, no cognitive overload, just **e**dit.
* **reducing typing errors** from 50% to 80% :
    <!-- * `emacs`: 80%, `nano`: 75%, `vim`: 66%, `vi`: 50%. -->
* and **increasing editing speed** by a factor 2 to 5 ;
    <!-- * `emacs`: 5×, `nano`: 4× `vim`: 3×, `vi`: 2×. -->
* **removing privileges issue** by invoking editor with adequate privileges ;
    * so you never again edit a file to finally realize that you didn't have enough privileges.

## Witchcraft! Shut up and take my money!

No needs my friends. Here is [the source](https://github.com/edouard-lopez/dotfiles/blob/master/.merc):

```bash
    # @description Edit given file with adequate rights (sudo/user)
    # @param    $@|$1  file(s) name
    # @return    void
    e() {
      f="$1"

      owner="$(stat -c '%G:%U' "$f")" # file ownership's information
      ownerUser="${owner%%:*}"
      ownerGroup="${owner##*:}"

      if [[ $ownerUser = 'root' || $ownerGroup = 'root' ]]; then
        sudo $EDITOR "$f"
      else
        $EDITOR "$f"
      fi
    }
```

Don't like `e` and prefer to use `v` ? 
No problem, there is room for improvement, feel free to [fork and submit pull requests](https://github.com/edouard-lopez/dotfiles/fork).
  
