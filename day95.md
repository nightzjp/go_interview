#### 1. 下面代码输出什么？请简要说明

```go
package main

import "fmt"

type foo struct{ Val int }

type bar struct{ Val int }

func main() {
	a := &foo{Val: 5}
	b := &foo{5}
	c := foo{Val: 5}
	d := bar{Val: 5}
	e := bar{Val: 5}
	f := bar{Val: 5}
	fmt.Println(a == b, c == foo(d), e == f)
}
```

#### 1. 答案&解析

```text
false true true

?
```

#### 2. 下面代码输出什么？

```go
package main

import (
	"fmt"
	"time"
)

func A() int {
	time.Sleep(100 * time.Millisecond)
	return 1
}

func B() int {
	time.Sleep(1000 * time.Millisecond)
	return 2
}

func main() {
	ch := make(chan int, 1)
	go func() {
		select {
		case ch <- A():
		case ch <- B():
		default:
			ch <- 3
		}
	}()
	fmt.Println(<-ch)
}
```

#### 2. 答案&解析

```text
1,2随机输出
select会随机选择一个case
```
