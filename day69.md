#### 1. 关于slice或map操作，正确的是？

```go
// A.
var s []int
s = append(s, 1)

// B.
var m map[string]int
m["one"] = 1

// C.
var s []int
s = make([]int, 0)
s = append(s, 1)

// D.
var m map[string]int
m = make(map[string]int)
m["one"] = 1
```

#### 1. 答案&解析

```text
ACD
```

#### 2. 下面代码输出什么？

```go
package main

import "fmt"

func test(x int) (func(), func()) {
	return func() {
			fmt.Println(x)
			x += 10
		}, func() {
			fmt.Println(x)
		}
}

func main() {
	a, b := test(100)
	a()
	b()
}
```

#### 2. 答案&解析

```text
100 110

闭包引用相同变量
```
