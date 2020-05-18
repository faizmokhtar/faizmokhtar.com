---
title: How to Completely Remove Git Submodules Within a Repository
date: 2020-05-18T14:13:29.189Z
categories:
  - tips
tags:
  - tips
  - git
comments: true
---
I found myself having to google this multiple times so I decide to write it here as a quick references for myself.

[Git submodules][1] is a way for you to keep a git repository as a subdirectory of another git repository. It's useful when you want to incorporate and keep track of external code or framework that your project depends on. It's like a poor man's version of `npm` or `cocoapods`.

Anyway, to add a git submodules is very easy. It's just simple a one liner. Eg:

```bash/shell
git submodule add git@github.com:faizmokhtar/example-repo library/example-submodule
```

That's it. But the steps to remove it are very tedious and it's something that I always forgot how to. So here are the steps to completely remove it from your repository.

## To Completely Remove Git Submodule

1. Open and edit the `.gitmodules` with your text editor.
2. Find and delete the relevant submodule lines:
   ```git
   [submodule "library/example-submodule"]
       path = library/example-submodule
       url = git@github.com:faizmokhtar/example-repo.git
   ```
3. Open and edit `.git/config` file.
4. Find and delete the relevant submodule lines:
   ```git
   [submodule "library/example-submodule"]
	url = git@github.com:faizmokhtar/example-repo.git
   ```
5. Delete the submodules.
   ```bash/shell
   $~ rm -rf library/example-submodule
   ```
6. Delete the files in `.git/modules`
   ```bash/shell
   $~ rm -rf .git/modules/example-submodule
   ```
7. Now, there should be some unstaged changes in your git staging area. Stage it and commit all the changes.

That should be it. Maybe you can turn this into a one liner bash script. 

Until next time. ✌️


[1]:https://github.blog/2016-02-01-working-with-submodules/
