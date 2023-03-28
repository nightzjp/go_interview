#### 1. 下面代码有什么问题？

```go
package main

type foo struct {
	bar int
}

func main() {
	var f foo
	f.bar, tmp := 1, 2
}
```

#### 1. 答案&解析

```text
:=操作符不能用于结构体字段赋值
```

#### 2. 下面的代码输出什么？

```go
package main

import "fmt"

func main() {
	fmt.Println(~2)
}
```

#### 2. 答案&解析

```text
编译错误。go语言中不可用~按位取反。go语言中使用^按位取反
```
