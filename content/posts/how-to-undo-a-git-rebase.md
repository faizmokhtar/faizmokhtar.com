---
title: "How to undo a git rebase"
date: 2020-11-05T03:15:13.196Z
comments: true
---
Given the following situation:

- You're on `feature/*` branch and you have your latest changes already pushed to `origin`
- Now, you want to rebase your `feature/*` branch with the latest `master`
- You type in `git rebase master` from your `feature/*` branch
- You fix all conflicts and finish the rebase
- OH SHIT SOMETHING'S WRONG I NEED TO UNDO IT BUT HOW?

Okay, take a deep breath and just calm down. Use the following to reset it to your latest origin.

```bash
$~ git reset --hard ORIG_HEAD
```

That's it. This will only work if you haven't push your changes to `origin` yet. If you have, then you need to use `git reflog`
