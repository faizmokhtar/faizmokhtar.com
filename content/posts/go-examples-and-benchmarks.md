---
title: "Go Examples and Benchmarks"
date: 2018-08-03T18:25:11+08:00
draft: false
tags: [go, til]
---

I learned about Go examples and benchmarks today. They are parts of Go default package testing.

## Examples
- Go `Examples` are executed just like tests
- They are compiled and optionally executed as part of unit tests
- It resides in the package `*_test.go` files

#### Structure

```
func ExampleRepeat() {
  repeated := Repeated("x", 5)
  fmt.Println(repeated)
  // output: xxxxx
}
```

#### Rules
- Function name must be prefix with `Example`
- It must have `// output: result`

#### How to Use
- to run the test with example, use: `go test -v`

#### Sample Execution

```
$ go test -v
=== RUN   TestRepeat
--- PASS: TestRepeat (0.00s)
=== RUN   ExampleRepeat
--- PASS: ExampleRepeat (0.00s)
```
#### Extras

- It will not run if you remove the `// output` comment.
- These examples can be display in `godoc` as part of the documentations
- To see the examples, run `go doc -http:6060` and navigate to `http://localhost:6060/pkg/` and you will find the examples in the package documentation.

--- 

## Benchmarks
- Just like `Examples` above, `Benchmarks` are executed by `go test`

#### Structure

```
func BenchmarkRepeat(b *testing.B) {
	for i := 0; i < b.N; i++ {
		Repeat("a", 100)
	}
}
```

#### Rules

- Function name must be prefix with `Benchmark`
- `testing.B` give you access to `b.N`.
- During benchmarking process, it will run `b.N` times and measure the duration it takes

#### How to Use

- To run the test with benchmarks, use: `go test -bench=.`

#### Sample Execution

```
$ go test -bench=.
goos: darwin
goarch: amd64
pkg: github.com/faizmokhtar/go-with-test/3-repeat
BenchmarkRepeat-8         300000              5485 ns/op
PASS
ok      github.com/faizmokhtar/go-with-test/3-repeat    1.714s
```

---

#### References:

1. https://golang.org/pkg/testing/#hdr-Benchmarks
2. https://dave.cheney.net/2013/06/30/how-to-write-benchmarks-in-go



