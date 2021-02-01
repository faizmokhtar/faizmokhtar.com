---
title: "How to list all the git commits history for a specific file"
date: 2020-12-16T02:24:09.782Z
categories:
  - git
tags:
  - git
comments: true
---
Assuming the following situation:

- You work on a large project that has an extensive git commits history and a lot of files
- You need to debug a certain issue that was caused by a certain file
- You look at the commits history to see which commit is causing the issue but going through it one by one is like finding a needle in a haystack

Well, worry not because you can use the following `git log` command to solve your issue:

```bash
$~ git log --follow -- path/to/file.txt
```

This will list down all the commits history for that specific file. It will work even if the file was deleted or renamed. However please be aware that it will only work for a single file at a time.
