#### 1. 下面的代码有几处语法问题，各式什么?

```go
package main

import "fmt"

func main() {
	var x string = nil
	if x == nil {
		x = "default"
	}
	fmt.Println(x)
}
```

#### 1. 答案&解析

```text
golang的字符串不能赋值为nil，也不能跟nil作比较
```

#### 2. return 之后的defer语句会执行吗？下面的代码会输出什么？

```go
package main

import "fmt"

var a bool = true

func main() {
	defer func() {
		fmt.Println("1")
	}()
	if a == true {
		fmt.Println("2")
		return
	}
	defer func() {
		fmt.Println("3")
	}()
}
```

#### 2. 答案&解析

```text
2 1

defer关键字后面的函数或方法想要执行必须先注册。return之后的语句是不能注册的。也就是不能执行后面的函数或方法
```
