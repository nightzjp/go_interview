#### 1. 下面这段代码输出什么？

```go
package main

import "fmt"

func main() {
	m := map[int]string{0: "zero", 1: "one"}
	for k, v := range m {
		fmt.Println(k, v)
	}
}
```

#### 1。 答案&解析

```text
map输出无序
```

#### 2. 下面这段代码输出什么？

```go
package main

import "fmt"

func calc(index string, a, b int) int {
	ret := a + b
	fmt.Println(index, a, b, ret)
	return ret
}

func main() {
	a := 1
	b := 2
	defer calc("1", a, calc("10", a, b))
	a = 0
	defer calc("2", a, calc("20", a, b))
	b = 1
}
```

```text
10 1 2 3
20 0 2 2
2 0 2 2
1 1 3 4

defer的参数如果是函数，会先执行。defer先进后出
```
