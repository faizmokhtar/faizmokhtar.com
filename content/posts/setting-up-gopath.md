---
title: "Setting Up $GOPATH"
date: 2018-08-02T17:48:22+08:00
draft: false
categories: [Development]
tags: [go]
---

GOPATH specifies the location of your `go` workspace. By default this will be `$HOME/go`.
You should set your `$GOPATH`  in `.zshrc` or `.bash_profile` to be used later in scripts or shell.

Add the followings into your `.bash_profile`:

```
export GOPATH=$HOME/go
export PATH=$PATH:$GOPATH/bin
```

Reload your shell and done.

To confirm that it's working, enter `$GOPATH` in your shell and it should take you to the `go` workspace directory.