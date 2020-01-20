---
title: go-delve issue on macOS Catalina
date: 2020-01-20T08:44:11.971Z
tags:
  - tools
  - go
comments: true
---
I started using Goland yesterday caused I heard good things about it from my friends who did Go development.

When I try to use the debugger functionality, I got the following error

```
could not launch process: debugserver or lldb-server not found: install XCode's command line tools or lldb-server
```

## How to Fix It?

When I googled, it seems this issue is related to go-delve and macOS Catalina. Running the following command on my terminal seems to fix it:

```
$~ xcode-select --install
```

Kind of weird since I always have XCode installed on my local machine and I'm pretty sure I have run the commands multiple times before. welp, as long as the issue is fix I should be glad. 🤷‍♂️
