#### 1. 下面这段代码输出什么？

```go
package main

import "fmt"

const (
	a = iota
	b = iota
)

const (
	name = "name"
	c    = iota
	d    = iota
)

func main() {
	fmt.Println(a, b, c, d)
}
```

#### 1. 答案&解析

```text
0 1 1 2

iota在const关键字出现时将被重置为0，const中每新增一行常量声明，iota计数一次
```

#### 2. 下面这段代码输出什么？

```go
package main

import "fmt"

type People interface {
	Show()
}

type Student struct{}

func (stu *Student) Show() {}

func main() {
	var s *Student
	if s == nil {
		fmt.Println("s is nil")
	} else {
		fmt.Println("s is not nil")
	}

	var p People = s
	if p == nil {
		fmt.Println("p is nil")
	} else {
		fmt.Println("p is not nil")
	}
}
```

#### 2. 答案&解析

```text
s is nil
p is not nil

当且仅当动态值和动态类型都为nil时，接口类型才为nil
```