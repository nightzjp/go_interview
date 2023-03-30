#### 1. n是秒数，下面代码输出什么？

```go
package main

import "fmt"

func main() {
	n := 43210
	fmt.Println(n/60*60, "hours and", n%60*60, "seconds")
}
```

#### 1. 答案&解析

```text
43200 hours and 600 seconds
运算符优先级
代码修复为：
package main

import "fmt"

func main() {
	n := 43210
	fmt.Println(n/(60*60), "hours and", n%(60*60), "seconds")
}
```

#### 2. 下面代码输出什么？

```go
package main

import "fmt"

const (
	Century = 100
	Decade  = 010
	Year    = 001
)

func main() {
	fmt.Println(Century + 2*Decade + 2*Year)
}
```

#### 2. 答案&解析

```text
118

go语言里面 八进制以0开头，十六进制以0x开头
```
