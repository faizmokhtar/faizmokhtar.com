---
title: Go Import Path Issue in VSCode
date: 2019-06-15T11:23:00.057Z
categories:
  - Development
tags:
  - go
  - tools
  - vscode
comments: true
---
I've been wondering for a while why `vscode` go extension always remove my local package imports on save.
Turns out it uses` goreturns` as a default formatters, not `gofmt`. Switch to `gofmt` and the problem goes away.
