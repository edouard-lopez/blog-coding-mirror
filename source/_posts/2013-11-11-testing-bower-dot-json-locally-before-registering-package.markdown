---
layout: post
title: "Testing bower.json locally before registering package"
date: 2013-11-11 19:30
comments: true
categories: [ bower, git, testing ]
published: true
---

Working on [Erase All the Kittens](https://github.com/SomeHats/Erase-All-Kittens) project to add support for [localization](https://github.com/fabi1cazenave/webL10n), I needed to create and test a local bower package. Here is how to do it.

## Bower

The big idea with [`bower`](https://github.com/bower/bower) is to easily share your projects' dependencies. So **using local repository should be limited to testing**.

Once you understand that, you should know that it is not –strictly– necessary to [`register` your package](https://github.com/bower/bower#registering-packages) in order to use it as a dependency.
This is due to the fact that `bower` dependencies can specify either a *version*, a *folder* or a _package_. So **you can use local repository**.

## Define as bower package

First you will need to [define your dependency as a bower package ](https://github.com/bower/bower#defining-a-package):

```bash
# create the bower package
cd /path/to/you-need-me
bower init
# answer questions…
```
## Add as project dependency

Then in your main project, the one that need the `you-need-me` dependency, edit `bower.json` file to add (or expand):

```json
      "dependencies": {
        …
        "you-need-me":  "file:///path/to/you-need-me/.git/"
        "you-need-me-windows":  "C:/path/to/you-need-me-windows/.git/"
      }
```

So you don't give a version, but an local `git` endpoint, i.e. **the subdirectory `.git/`**.

## Install dependency

In the man project install bower dependencies with:

```bash
cd /path/to/main-project/
bower install
```
### Failure

```bash
bower you-need-me#*              ENOTFOUND Package /path/to/you-need-me/ not found
```
Check again your path and that you point to the `.git/` directory of your dependency.

### Success

You should get something like:

```bash
bower you-need-me#*             not-cached file:///path/to/you-need-me/.git/#*
bower you-need-me#*                resolve file:///path/to/you-need-me/.git/#*
bower you-need-me#*               checkout master
bower you-need-me#*               resolved file:///path/to/you-need-me/.git/#b18c753c6f
bower you-need-me#*                install you-need-me#b18c753c6f
```

# Registering package

Registering is quite simple and you should [know the prerequisites before doing it](https://github.com/bower/bower#registering-packages):

>    There **must** be a valid manifest JSON in the current working directory.
>    Your package should use [semver](http://semver.org/) Git tags.
>    Your package **must** be available at a Git endpoint (e.g., GitHub); remember to push your Git tags!

To register, specify the end point and the endpoint to use to fetch the dependency (i.e. `git clone`):

```bash
bower register fake-projet git@github.com:anonymous/fake-projet.git
```
