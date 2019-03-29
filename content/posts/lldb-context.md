---
title: "Understanding LLDB Contexts in Xcode"
date: 2019-03-26T16:35:41+08:00
categories: [little-bites]
tags: [lldb, xcode, ios, debugging]
draft: false
---

Sometimes when debugging on Xcode with LLDB's `p` or `po`, it will throw a syntax error at you and you might be wondering out why? You checked for any typos but everything seems to be correct. So what gives?

Well, that's because you might be using it in the wrong context.

Here's a quick rundown:

1. When you stop in Objective-C code using breakpoint, LLDB will use Objective-C debugging context.

    So you have to use Objective-C syntax to debug:
    ```
    (lldb) po [ViewController description]
    ```
2. Similarly when you add a breakpoint in Swift code, LLDB will use Swift debugging context instead.

    So you have to use Swift syntax to debug:
    ```
    (lldb) po ViewController.description()
    ```

3. And finally, Xcode will always use Objective-C as the default context. Meaning if you pause the program execution without using breakpoint, you'll have to use Objective-C syntax.

That's it. Hopefully this tips will helps you a little bit when debugging a project that have a mixture of both Swift and Objective-C codes. ✌️

