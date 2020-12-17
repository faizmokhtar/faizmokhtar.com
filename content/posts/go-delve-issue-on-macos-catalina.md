---
title: "How to fix Go Delve debugger issue on macOS Catalina"
date: 2020-01-20T08:44:11.971Z
tags:
  - tools
  - go
  - debugging
comments: true
---
I started using [GoLand](https://www.jetbrains.com/go/) yesterday after hearing good things about it from my friends who is doing Go development.

When I try to use the GoLand's debugger, I got the following error;


> could not launch process: debugserver or lldb-server not found: install XCode's command line tools or lldb-server


## How Do I Fix It?

When I googled, it seems this issue is more related to [Delve](https://github.com/go-delve/delve), the debugger for Go and macOS Catalina. Running the following command on my terminal will fix it

```
$~ xcode-select --install
```

It's quite weird as I always have Xcode installed on my local machine and I'm pretty sure I have ran the commands multiple times before. welp. 🤷‍♂️
