---
title: "How to install latest stable ruby version with rbenv"
date: 2020-08-18T03:25:27.391Z
categories:
  - ""
tags:
  - ruby
comments: true
---
Today I learned a simple solution to install the latest stable [ruby][2] version with [rbenv][1]. If you are using [rbenv][1] to maintain your ruby versions but you couldn't be bothered to keep track of the releases and just want a stable version, you can use the following command:

````
$ rbenv install $(rbenv install -l | grep -v - | tail -1)
````

This command will get the latest stable ruby release and install it with `rbenv install`. That's it.

**References**: https://stackoverflow.com/questions/30179484/install-latest-stable-version-of-ruby-using-rbenv

[1]: https://github.com/rbenv/rbenv
[2]: https://ruby-doc.org/