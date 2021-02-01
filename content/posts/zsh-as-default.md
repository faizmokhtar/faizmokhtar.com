---
title: "How to set zsh as the default terminal shell"
date: 2018-08-20T22:41:07+08:00
draft: false
categories: [Development]
tags: [tools]
---

I prefer [`zsh`][1] over [`bash`][2] as my everyday shell.
Unfortunately [`zsh`][1] is not the default shell on macOS.

To make it as a default shell for your machine, simply do the following:

## 1. Install `zsh`

Make sure zsh is available on your system. If not, install it with [`brew`][3].

```bash
$~ brew install zsh

$~ which zsh
/usr/local/bin/zsh #output
```

## 2. Set `zsh` as default shell

To set is as default shell, run the following in your terminal:

```bash
$~ sudo sh -c "echo $(which zsh) >> /etc/shells"
$~ chsh -s $(which zsh)
```

Then, simply reopen your shell again and it should used [`zsh`][1] as the default shell. That's it.

### To check which shell you're using

If you are still unsure whether your shell is running [`zsh`][1] or [`bash`][2], run the following in your terminal:

```bash
$~ echo $0
-zsh  #output
```

<center>✌️</center>

[1]:http://www.zsh.org/
[2]:https://www.gnu.org/software/bash/
[3]:https://brew.sh/