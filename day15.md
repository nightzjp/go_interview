#### 1. 下面代码的下划线处可以填入哪个选项？

```go
func main() {
	var s1 []int
	var s2 = []int{}
	if _ == nil {
		fmt.Println("yes nil")
	} else {
		fmt.Println("no nil")
	}
}
// A. s1
// B. s2
// C. s1,s2都可以
```

#### 1。 答案&解析

```text
A。

nil切片和空切片相等，空切片跟nil不相等
```

#### 2. 下面这段代码输出什么？

```go
package main

import "fmt"

func main() {
	i := 65
	fmt.Println(string(i))
}

// A. A
// B. 65
// C. compilation error
```

#### 2. 答案&解析

```text
A。

utf-8编码中，十进制数字65对应的符号是A
```

#### 3. 下面这段代码输出什么？

```go
package main

import "fmt"

type A interface {
	ShowA() int
}

type B interface {
	ShowB() int
}

type Work struct {
	i int
}

func (w Work) ShowA() int {
	return w.i + 10
}

func (w Work) ShowB() int {
	return w.i + 20
}

func main() {
	c := Work{3}
	var a A = c
	var b B = c
	fmt.Println(a.ShowA())
	fmt.Println(b.ShowB())
}
```

#### 3. 答案&解析

```text
13 23

一种类型实现多个接口，结构体Work分别实现了A、B，所以接口变量a、b调用各自的方法ShowA()和ShowB()
```
