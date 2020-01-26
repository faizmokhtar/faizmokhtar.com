---
title: How To Enable Go Fmt On Save In GoLand
date: 2020-01-26T04:12:02.784Z
categories:
  - ''
tags:
  - tools
  - go
comments: true
---
One thing I miss when switching from VS Code to GoLand is the ability to auto-format the code with [`go fmt`][1] when saving the files.

You need to navigate to `Tools > Go Tools > Go Fmt Project` to run it, or use the keyboard shortcut which is <kbd>⌥⇧⌘P</kbd>. Still, this is something that you can easily forget to run every single time.

Luckily, GoLand have built in [file watchers][2] that you can use to run `go fmt` every time there's a file changes.

Here's how;

1. Go to `Preferences > Tools > File Watchers`
2. Click on the `Add` button and choose `go fmt`
3. Click on the `OK` button to enable it 

![How to set Goland File Watchers to run go fmt](/images/uploads/goland-gofmt.png "How to set Goland File Watchers to run go fmt")

That's it. Now, when you saved your code, the [file watchers][2] will detect this changes and run `go fmt`. You can even use the [file watchers][2] to run `goimports`, `go vet` or anything else that you think make sense.

##### Resources:
1. [GoLand integrations with go tools][3]
2. [Goland file watchers][4]

[1]:https://golang.org/cmd/gofmt/
[2]:https://www.jetbrains.com/help/go/settings-tools-file-watchers.html
[3]:https://www.jetbrains.com/help/go/integration-with-go-tools.html
[4]:https://www.jetbrains.com/help/go/settings-tools-file-watchers.html
