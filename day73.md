#### 1. 下面代码输出什么？

```go
package main

import "fmt"

func test() []func() {
	var funs []func()
	for i := 0; i < 2; i++ {
		funs = append(funs, func() {
			fmt.Println(&i, i)
		})
	}
	return funs
}

func main() {
	funs := test()
	for _, f := range funs {
		f()
	}
}
```

#### 1. 答案&解析

```text
0xc00001a0a8 2
0xc00001a0a8 2

闭包延迟求值。for循环局部变量i，匿名函数每一次使用的都是同一个变量
```

#### 2. 下面的代码能编译通过吗？可以的话输出什么？

```go
package main

import "fmt"

var f = func(i int) {
	fmt.Println("x")
}

func main() {
	f := func(i int) {
		fmt.Println(i)
		if i > 0 {
			f(i - 1)
		}
	}
	f(10)
}
```

#### 2. 答案&解析

```text
10
x
```
