#### 1. 下面选项正确的是？

```go
// A. 类型可以声明在函数体内
// B. go语言支持++i或者--i的操作
// C. nil是关键字
// D. 匿名函数可以直接赋值给一个变量或者直接执行
```

#### 1. 答案&解析

```text
AD
```

#### 2. 下面的代码输出什么？

```go
package main

import "fmt"

func F(n int) func() int {
	return func() int {
		n++
		return n
	}
}

func main() {
	f := F(5)
	defer func() {
		fmt.Println(f())
	}()
	defer fmt.Println(f())
	i := f()
	fmt.Println(i)
}
```

#### 2. 答案&解析

```text
7 6 8

匿名函数、defer()，defer后边的函数如果带参数，会优先计算参数
```
