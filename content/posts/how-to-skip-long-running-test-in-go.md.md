---
title: How to Skip Long Running Test in Go
date: 2020-02-23T02:41:00.347Z
categories:
  - little-bites
tags:
  - go
comments: true
---
Here's a quick tip on how to skip long running tests in Go. 

In your long running test, add a `t.Short()` boolean check. 

For example:
```go
func TestLongRunning(t *testing.T) {
    if t.Short() {
        t.Skip("skip long running test")
    }
    // tests that will take a while to run
    ...
}
```

Then when you run `go test`, provide a `-short` flag to skip this test.

For example:
```
$~ go test -v -short
```

You can confirm this behaviour by checking test output. You should see `skipping long running test in short mode` message in the output.

For example:
```
--- SKIP: TestLongRunningTest (0.00s)
    main_test.go:27: skipping long running test in short mode
PASS
ok      github.com/faizmokhtar/toytesting       0.385s
```

That's it. Hope you will find this tip to be useful.

References:
1. [Go' testing **Short** documentation](https://golang.org/pkg/testing/#Short)
2. [Stack Overflow - Skip some tests with Go](https://stackoverflow.com/questions/24030059/skip-some-tests-with-go-test)
