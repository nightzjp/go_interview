#### 1. 下面代码输出什么？

```go
package main

import "fmt"

type S1 struct{}

func (s S1) f() {
	fmt.Println("S1.f()")
}

func (s S1) g() {
	fmt.Println("S1.g()")
}

type S2 struct {
	S1
}

func (s S2) f() {
	fmt.Println("S2.f()")
}

type I interface {
	f()
}

func printType(i I) {
	fmt.Printf("%T\n", i)
	if s1, ok := i.(S1); ok {
		s1.f()
		s1.g()
	}
	if s2, ok := i.(S2); ok {
		s2.f()
		s2.g()
	}
}

func main() {
	printType(S1{})
	printType(S2{})
}
```

#### 1. 答案&解析

```text
main.S1
S1.f()
S1.g()
main.S2
S2.f()
S1.g()

类型断言，结构体嵌套。
结构体S2嵌套了结构体S1，S2自己没有实现g(),调用的是S1的g()
```

#### 2. 下面代码有什么问题？

```go
package main

import (
	"fmt"
	"sync"
)

func main() {
	var wg sync.WaitGroup
	wg.Add(1)
	go func() {
		fmt.Println("1")
		wg.Done()
		wg.Add(1)
	}()
	wg.Wait()
}
```

#### 2. 答案&解析

```text
协程里面，使用wg.Add(1)但是没有wg.Done(),导致panic()
```
