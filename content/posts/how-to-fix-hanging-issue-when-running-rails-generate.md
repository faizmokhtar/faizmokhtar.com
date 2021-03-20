---
title: How to fix hanging issue when running rails generate
date: 2021-03-20T04:29:00.063Z
tags:
  - tools
  - rails
comments: true
---
I've been experiencing some annoying issues when trying to run `rails generate` or `rails console` lately. These commands will sometimes get stuck indefinitely. To fix this issue, simply run the following:

```
$~ spring stop
```

Once you run it, try running the previous command again and it should work. I'm still not sure why it happened but for now, this temporary solution should reduce the annoyances.