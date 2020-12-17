---
title: "How to use Go Dep to manage dependencies"
date: 2019-02-11T22:09:13+08:00
draft: false
categories: [Development]
tags: [go, til]
---

 [`dep`][1]  is a dependency management tool for golang. If you have done any software development before,
 [`dep`][1] is similar to [`npm`][2], [`pod`][3] or [`pip`][4]. In simple words, it is a package manager to manage
 your project's third party libraries.

# How to install it

There's a few ways to install [`dep`][1]. Personally I prefer to install it with [`Homebrew`][5]

```
$~ brew install dep
```

# Initializing a project with [`dep`][1]

To initialize it in your `go` project, go to your project directory and run the following

```
$~ dep init
```

This will create three things in your directory

1. `Gopkg.toml`: This where you specifies the project dependencies
2. `Gopkg.lock`: File generated as a result from running `dep`. It's a complete dependency graph for your project.
You shouldn't edit this manually.
3. `vendor/`: This is where the dependencies are stored

`dep init` will behave differently depending on the state of your project.

If it is a **new project**, `Gopkg.toml` and `vendor/` will be essentially empty aside 
from the usual commented out guides on how to use it.

If it is an **existing project**, `Gopkg.toml` adn `vendor/` will add all the dependencies 
that you have added in your project with `go get`.

# How to use [`dep`][1]?

### Adding a new depencies

To add a new depencies in your project, run the following

```
$~ dep ensure -add <DEPENDENCIES>
```

Replace `<DEPENDENCIES>` with the path to its project repo. For example

```
$~ dep ensure -add github.com/gorilla/mux
```

### Others

A few more commands that I find useful:

1. `dep status`: Will report the status of your project dependencies
2. `dep prune`: Will tell you which libraries that are out of sync


# Conclusion

I am sure by now you are asking **"why should I use `go dep` when go already comes with `go get`?"**.

Well, imagine you are working in a team project that uses a lot of dependencies. 
Each having their own version of libraries. Pretty soon you will have those
"Works on my machine!" real quick.

`dep` solve this by making sure everyone who works on the project is guaranteed to be
using the same version of dependencies.

That's it. Hopefully now you have learned the basic usage sof `go dep` to manage your project dependencies.

 [1]:https://golang.github.io/dep/
 [2]:https://www.npmjs.com/
 [3]:https://cocoapods.org/
 [4]:https://packaging.python.org/tutorials/installing-packages/
 [5]:https://brew.sh/



