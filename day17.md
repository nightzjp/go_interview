#### 1. 下面代码中，x已经声明，y没有声明，请判断每条语句的对错

```go
// A. x, _ := f()
// B. x, _ = f()
// C. x, y := f()
// D. x, y = f()
```

#### 1. 答案&解析

```text
错、对、对、错
```

#### 2. 下面代码输出什么？

```go
package main

import "fmt"

func increaseA() int {
	var i int
	defer func() {
		i++
	}()
	return i
}

func increaseB() (r int) {
	defer func() {
		r++
	}()
	return r
}

func main() {
	fmt.Println(increaseA())
	fmt.Println(increaseB())
}

// A. 1 1
// B. 0 1
// C. 1 0
// D. 0 0
```

#### 2. 答案&解析

```text
B。

匿名返回值&命名返回值的区别
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
	var a A = Work{3}
	s := a.(Work)
	fmt.Println(s.ShowA())
	fmt.Println(s.ShowB())
}

// A. 13 23
// B. compilation error
```

#### 2. 答案&解析

```text
A。 

a类型断言为Work
```
