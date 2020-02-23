---
title: How to Skip Long Running Test in Go
date: 2020-02-23T02:41:00.347Z
categories:
  - little-bites
tags:
  - go
comments: true
---
In Go `testing` package, there is a way for you to skip a long running tests by providing a `-short` flag.

```go
func TestLongRunning(t *testing.T) {
    if t.Short() {
        t.Skip("skip long running test")
    }
    // tests that will take a while to run
    ...
}
```

To skip it, provide a `-short` flag in `go test`
```
$~ go test -short
```


References:
1. https://golang.org/pkg/testing/#Short
