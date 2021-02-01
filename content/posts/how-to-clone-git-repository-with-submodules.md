---
title: "How to clone a git repository that have submodules"
date: 2020-08-16T16:13:21.548Z
tags:
  - git
comments: true
---
Today I learned how to git clone a repository that has [git submodules][1] inside of it. I realized that when I cloned a project it will clone the parent repo but the submodules will be empty. Here are the steps on how to clone it properly.

If you haven't cloned the repository yet, you can use `--recurse-submodules` option:

````bash
$ git clone --recurse-submodules https://github.com/sample/sample-repo.git
````

Otherwise, If you already cloned the project then you can use the following command. Run the command inside your git repository.

````bash
$ git submodule update --init --recursive
````

This will initialize, fetch and checkout any nested submodules for the repository. That's it.

[1]: https://git-scm.com/book/en/v2/Git-Tools-Submodules