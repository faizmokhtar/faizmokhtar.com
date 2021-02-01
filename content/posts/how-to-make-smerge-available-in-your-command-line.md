---
title: "How to make smerge available in your command line "
date: 2020-09-04T01:47:22.001Z
tags:
  - tools
comments: true
---
`smerge` is a command line tools for [Sublime Merge][1]. To make this tools available in your command line, you have to symlink it. Here's the command on how to do it for macOS:

```bash
 ln -s "/Applications/Sublime Merge.app/Contents/SharedSupport/bin/smerge" /usr/local/bin/smerge
``` 

That's it. After this, you can easily browse your repo in Sublime Merge just by typing `smerge` in your CLI.

For Windows or Linux, you can check Sublime Merge's [docs][2].

[1]:https://www.sublimemerge.com/
[2]:https://www.sublimemerge.com/docs/command_line