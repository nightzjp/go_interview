#### 1. 下面代码能否正确输出？

```go
package main

import "fmt"

func main() {
	var fn1 = func() {}
	var fn2 = func() {}
	if fn1 != fn2 {
		fmt.Println("fn1 not equal fn2")
	}
}
```

#### 1. 答案&解析

```text
函数只能与nil进行比较。不能与函数比较
```

#### 2. 下面代码输出什么？

```go
package main

import "fmt"

type T struct {
	n int
}

func main() {
	m := make(map[int]T)
	m[0].n = 1
	fmt.Println(m[0].n)
}

// A. 1
// B. compilation error
```

#### 2. 答案&解析

```text
B.

map中的value不可寻址
可修复为：
package main

import "fmt"

type T struct {
	n int
}

func main() {
	m := make(map[int]T)
	t := T{1}
	m[0] = t
	fmt.Println(m[0].n)
}
```
