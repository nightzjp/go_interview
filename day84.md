#### 1. 函数执行时，如果由于panic导致了异常，则延迟函数不会执行，这一说法是否正确?

```go
// A. true
// B. false
```

#### 1. 答案&解析

```text
B

由panic引发异常之后，程序停止执行，然后调用延迟函数，就想程序正常退出一样。
```

#### 2. 下面代码输出什么？

```go
package main

import "fmt"

func main() {
	a := [3]int{0, 1, 2}
	s := a[1:2]

	s[0] = 11
	s = append(s, 12)
	s = append(s, 13)
	s[0] = 21

	fmt.Println(a)
	fmt.Println(s)
}
```

#### 2. 答案&解析

```text
[0 11 12]
[21 12 13]
```