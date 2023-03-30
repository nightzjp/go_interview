#### 1. 关于switch语句，下面说法正确的是？

```go
// A. 单个case中，可以出现多个结果选项
// B. 需要使用break来明确退出一个case
// C. 只有在case中明确添加fallthrought关键字，才会执行紧跟的下一个case
// D. 添加表达式必须为常量或者整数
```

#### 1. 答案&解析

```text
AC.
```

#### 2. 下面代码能编译通过吗？如果可以输出什么？

```go
package main

import "fmt"

func alwaysFalse() bool {
	return false
}

func main() {
	switch alwaysFalse() {
	case true:
		fmt.Println(true)
	case false:
		fmt.Println(false)
	}
}
```

#### 2. 答案&解析

```text
编译通过，输出false
```
