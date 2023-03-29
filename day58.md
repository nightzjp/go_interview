#### 1. 下面的代码输出什么？

```go
package main

import "fmt"

type T struct {
	x int
	y *int
}

func main() {
	i := 20
	t := T{10, &i}

	p := &t.x

	*p++
	*p--

	t.y = p
	fmt.Println(*t.y)
}
```

#### 1. 答案&解析

```text
10.
```

#### 2. 下面哪一行代码会引发panic，请说明原因

```go
package main

func main() {
	x := make([]int, 2, 10)
	_ = x[6:10]
	_ = x[6:]
	_ = x[2:]
}
```

#### 2. 答案&解析

```text
第6行

截取符合[i:j],如果j省略，默认是原切片的长度，x的长度为2.小于初始下标6，引发panic
```
