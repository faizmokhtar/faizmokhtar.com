---
title: "View Git Diff of Changes Since Last Pull"
date: 2018-08-07T17:32:55+08:00
draft: false
tags: [git, til]
---

To view the changes between your last `git pull`

```
$~ git pull origin
$~ git diff @{1}..
```

`@{n}` means the n-th previous value of `HEAD`. You can refer the official docs on [reflog Shortnames][1] for more.

**p/s**: I am currently trying to dissociate myself from becoming too dependent on [SourceTree][2] for daily git operations.

[1]:https://git-scm.com/book/en/v2/Git-Tools-Revision-Selection
[2]:https://www.sourcetreeapp.com