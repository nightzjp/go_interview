#### 1. 下面这段代码输出什么？

```go
package main

import "fmt"

func main() {
	a := 2 ^ 15
	b := 4 ^ 15
	if a > b {
		fmt.Println("a")
	} else {
		fmt.Println("b")
	}
}
```

#### 1. 答案&解析

```text
a

go语言里面的^表示按位异或，而不是求幂
```

#### 2. 下面那些函数不能编译通过？

```go
func A(string string) string {
	return string + string
}

func B(len int) int {
	return len + len
}

func C(val, default string) string {
	if val == "" {
		return default
	}
	return val
}
```

#### 2. 答案&解析

```text
C()函数编译报错。default属于关键字。string和len属于预定义标识符，可以在局部使用
```
