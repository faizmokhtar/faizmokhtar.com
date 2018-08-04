---
title: "On Writing Tests"
date: 2018-08-04T23:07:06+08:00
draft: false
---

I would consider that I am a beginner at [unit testing][1] but these days, I started writing it much more frequently and I am quite proud of it. 
I noticed that it actually helps me to notice regression early on and as well as helping me to understand how the components work together.

I also learned 'the hard way' how hard it is to start writing unit tests for an existing project that have 0 unit test. Like super hard.
Still, I find it to be an interesting challenge for me to grow as a software developer.

So here are some helpful advice if you're stuck in the same situation and wanted to make the project better.

## 1. Start Small
Don't rewrite all the existing methods using TDD, BDD or whatever. Instead when you find a bug in the code, try write a failing test
for the bug and make the test pass first. Try to improve the code when you have the time and make sure that this bug never returns again.
You don't have to ask your project manager to allocate a time slots for this and the changes doesn't have to be big. 

You just have start writing a single unit test and the rest will follow.

## 2. Write New Feature With Unit Tests
When you are given the responsibity to add new feature, try to write a unit tests alongside it. It will not work all the time as you realize
that there might be a lot of coupling between each classes or methods, or heavy usage of singletons. but you just have to try. If you can't,
take some time to think about the changes to be done to make it more testable.

## 3. It Doesn't Have to Be Perfect
Your unit tests doesn't have to be perfect, it just need to be correct. I read that a nonperfect test is better than no test at all
and as the more tests you add, the better your tests will become. You just have to keep on adding tests and continously improve it along the way.

## 4. Enable Code Coverage
try to enable the code coverage feature available on your IDE. I find it somewhat motivating to see the code coverage percentage increase 
from 0%, 5%, 18.5%...well you got the gist of it. As you progress, the code will naturally becomes easier to test and more modular.

Good luck. 🐛

[1]: https://en.wikipedia.org/wiki/Unit_testing