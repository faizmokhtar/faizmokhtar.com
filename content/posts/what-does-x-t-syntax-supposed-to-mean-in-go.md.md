---
title: What does `x.(T)` syntax supposed to mean in Go?
date: 2020-04-14T14:33:00.667Z
categories:
  - little-bites
tags:
  - go
  - til
comments: true
---
It is called [type assertion][1]. Here is how it looks like:

```
str := value.(string)
```

It gives you access to the interface's concrete value. It asserts the values stored in `x` is of type `T` and that `x` is not nil.

Type assertion can also return two values: the concrete underlying value and a boolean value that check if the assertion is true.

```
t, ok := x.(T)
```

Here is some code examples for a much easier references. It is a similar example as the one you can find in [A Tour of Go][1]

```
    var i interface{} = "hello"

    s := i.(string)
    fmt.Println(s)
    // Will prints out: hello

    s, ok := i.(string)
    fmt.Println(s, ok)
    // Will prints out: hello, true

    f, ok := i.(float64)
    fmt.Println(f, ok)
    // Will prints out: 0, false

    f = i.(float64)
    fmt.Println(f)
    // Will cause "panic"
    // panic: interface conversion: interface {} is string, not float64
```

### Additional references:

- [What is the meaning of “dot parenthesis” syntax in Golang?][2]
- [What does “i.(string)” actually mean in golang syntax?][3]
- [Go Type Assertion's spec][4]
- [Effective Go - Interface conversions and type assertions][5]



[1]: https://tour.golang.org/methods/15
[2]: https://stackoverflow.com/questions/24492868/what-is-the-meaning-of-dot-parenthesis-syntax-in-golang
[3]: https://stackoverflow.com/questions/53577949/what-does-i-string-actually-mean-in-golang-syntax?noredirect=1&lq=1
[4]: https://golang.org/ref/spec#Type_assertions
[5]: https://golang.org/doc/effective_go.html#interface_conversions
