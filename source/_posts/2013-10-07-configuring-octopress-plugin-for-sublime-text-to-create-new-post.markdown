---
layout: post
title: "Configuring Octopress plugin for Sublime Text to create new post"
date: 2013-10-07 11:31
comments: true
tags: [ solved, sublime-text, octopress, configuration ]
categories: [ solved, sublime-text, octopress, configuration ]
---

[Octopress](http://octopress.org/) is a blog framework build on top of [Jekyll](http://github.com/mojombo/jekyll), the blog-aware static site generator powering [Github Pages](http://pages.github.com/). So it's a blog's boilerplate working with [Markdown](http://daringfireball.net/projects/markdown/basics) documents.
<!--more-->
Assuming you didn't already installed [`Octopress` plugin for Sublime Text 2](https://github.com/blueplanet/sublime-text-2-octopress), you can install it using [Package Control](https://sublime.wbond.net/).

## Sublime Text Configuration

In `Sublime Text` you've a great deal of way to [customize your experience, and your projects](www.sublimetext.com/docs/2/projects.html):

> sublime-project files are JSON, and support three top level sections: folders, for the included folders, 
> settings, for file-setting overrides, and build_systems, for project specific build systems.

## Creating new post Issue

However when attempting to create new post,  the `Octopress` plugin **doesn't seem to comply to this** expectation

{% img left /images/screenshots/octopress-create-new-post.png 'Creating new post with Octopress plugin for sublime text' %}

I kept having the following error as well as plenty of shell interpretation errors in `Sublime Text` console:

```text
    error: Octopress exec failed. Please check octopress env, and try again.
    You can check exec log in sublime console.
```

## Solution

All this was due to a misconfiguration as for your configuration to be taken into account you **must set your configurations in the Octopress' _Settings – User_ file**. You can edit this file via the menu `Preferences` → `Package Settings` → `Octopress` → `Settings - User` and paste:

```json
    {
      // path to your octopress
      "octopress_path": "/path/to/your/blog-dir",
    
      // the shell to run commands with
      "octopress_shell_executable": "/bin/zsh",
    
      // command to run before calling rake, eg source ~/bash_profile to set up your local environment inc paths to ruby, rake etc.
      "octopress_cmd_before_rake" : "export PATH=$PATH:$HOME/.rvm/bin; source $HOME/.rvm/scripts/rvm && export GEM_HOME=$HOME/.rvm/gems/ruby-1.9.3-p448",
    
      // set to generate, deploy or generate_and_deploy if you wish to have your changes generated into the /public folder and/or deployed upon file save
      "octopress_onsave_action": "generate",
    
      // set to the extension of all new pages. This should be the same as in your Rakefile setting for new_page_ext
      "octopress_page_extension": "md"
    }
```
More options are available in the _Settings – Default_ file, which you will edit in a similar way.

### `octopress_path` tweak

Being familiar with shell programming I tried to use `$HOME` variable in `octopress_path` value but this throw an error:
```text
OSError: [Errno 2] No such file or directory: '$HOME/path/to/blog/'
```
So I fall back to a complete path.

### `octopress_cmd_before_rake` tweak

The value of `octopress_cmd_before_rake` was also problematic as sourcing `~/.zshrc` was throwing plenty of error, I narrowed it down to :

1. Export the path to `rvm` bin: 
```bash
export PATH=$PATH:$HOME/.rvm/bin;
```
2. Source only the `rvm` configuration file:
```bash
source $HOME/.rvm/scripts/rvm
```
3. The export the `GEM_HOME` set to the correct `ruby`  version:
```bash
export GEM_HOME=$HOME/.rvm/gems/ruby-1.9.3-p448
```

## References

* **[ja]** [Github Pages+OctopressでBlog作成](http://amacbee.github.io/blog/2013/05/26/1/) by [@beeEaMa](http://twitter.com/beeEaMa) ;
* [Project-Specific Settings Override](http://www.sublimetext.com/forum/viewtopic.php?f=2&t=11335) thread.
