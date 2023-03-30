#### 1. 下面代码能编译通过吗？请简要说明

```go
package main

import "fmt"

func main() {
	v := []int{1, 2, 3}
	for i, n := 0, len(v); i < n; i++ {
		v = append(v, i)
	}
	fmt.Println(v)
}
```

#### 1. 答案&解析

```text
能编译通过， 输出[1 2 3 0 1 2]

for循环开始的时候，终止条件只会计算一次
```

#### 2. 下面代码输出什么？

```go
package main

import "fmt"

type P *int
type Q *int

func main() {
	var p P = new(int)
	*p += 8
	var x *int = p
	var q Q = x
	*q++
	fmt.Println(*p, *q)
}

// A. 8 8
// B. 8 9
// C. 9 9
```

#### 2. 答案&解析

```text
C

指针变量指向相同的地址
```
