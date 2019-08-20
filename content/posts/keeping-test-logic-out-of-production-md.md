---
title: Keeping Test Logic out of Production
date: 2019-08-20T14:33:34.517Z
categories:
  - Reading Notes
tags:
  - notes
  - til
comments: false
---
I'm currently reading [xUnit Test Patterns: Refactoring Test code][1] and so far it's been a great read.

Here's some advices on keeping the test logic out of production code. Don't.

> Testing is about verifying the behavior of a system. If the system behaves differently when under test, then how can we be certain that the production code actually works?

> The production code should not contain any conditional statements of the `if testing then` sort. It should not contain any test logic at all.

> - [xUnit Test Patterns][1], chapter 5

[1]:http://xunitpatterns.com/
