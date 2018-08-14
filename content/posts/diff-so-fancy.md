---
title: "Diff So Fancy"
date: 2018-08-13T16:37:39+08:00
draft: false
tags: [git, tools]
---

I find it quite hard to make sense of the output from `git diff`. Let's just say that it is somewhat off-putting. [`diff-so-fancy`][1] is an open source project to solve this problem and help make your diff much less uglier.

## Installation

There are a lot of ways to install it but I prefer to install all my tools with Brew. 
So run the following in your terminal:

```
$~ brew install diff-so-fancy
```

## Configuration

To use `diff-so-fancy`, you have to set it up globally. Run the following:

```
$~ git config --global core.pager "diff-so-fancy | less --tabs=4 -RFX"
```

This will change your `~/.gitconfig` like so

```
[core]
    ... // other settings
    pager = diff-so-fancy | less --tabs=4 -RFX
```

When you run `git diff`, you will noticed how much of an improvement that `diff-so-fancy`
brings. There are a few more customizations that can be done. Try it on your own.

[1]:https://github.com/so-fancy/diff-so-fancy
