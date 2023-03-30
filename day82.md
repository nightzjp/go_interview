#### 1. 下面这段代码输出什么？

```go
package main

import "fmt"

func main() {
	count := 0
	for i := range [256]struct{}{} {
		m, n := byte(i), int8(i)
		if n == -n {
			count++
		}
		if m == -m {
			count++
		}
	}
	fmt.Println(count)
}
```

#### 1. 答案&解析

```text
4.

数值溢出。当i的值为0,128会发生相等情况，byte是int8的别名
```

#### 2. 下面代码输出什么？

```go
package main

import "fmt"

const (
	azero = iota
	aone  = iota
)

const (
	info  = "msg"
	bzero = iota
	bone  = iota
)

func main() {
	fmt.Println(azero, aone)
	fmt.Println(bzero, bone)
}
```

#### 2. 答案&解析

```text
0 1
1 2

iota的使用：iota出现在const语句的时候会被重置
```
