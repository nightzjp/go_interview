#### 1. 切片a、b、c的长度和容量分别是多少？

```go
package main

import "fmt"

func main() {
	s := [3]int{1, 2, 3}
	a := s[:0]
	b := s[:2]
	c := s[1:2:cap(s)]
	fmt.Println(len(a), cap(a))
	fmt.Println(len(b), cap(b))
	fmt.Println(len(c), cap(c))
}
```

#### 1. 答案&解析

```text
0 3, 2 3, 1 2

[i:j:k]
长度：j-i
容量：k-i
```

#### 2. 下面代码中A B两处应该怎么修改才能顺利编译？

```go
package main

import "fmt"

func main() {
	var m map[string]int // A
	m["a"] = 1
	if v := m["b"]; v != nil { // B
		fmt.Println(v)
	}
}
```

#### 2. 答案&解析

```text
package main

import "fmt"

func main() {
	m := make(map[string]int) // A
	m["a"] = 1
	if v, ok := m["b"]; ok { // B
		fmt.Println(v)
	}
}

A 只声明未赋值
B 当元素不存在的时候，v会返回对应的零值
```

#### 3. 下面代码输出什么？

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
	fmt.Println(a.ShowB())
	fmt.Println(b.ShowA())
}
// A. 23 13
// B. compilation error
```

#### 3. 答案&解析

```text
B。

...
接口A不包括ShowB()，接口B也不包括ShowA() 编译报错
```
