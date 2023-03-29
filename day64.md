#### 1. recover()的调用方式正确的是？

```go
package main

// A.
func main() {
	recover()
	panic(1)
}

// B.
func main() {
	defer recover()
	panic(1)
}

// C.
func main() {
	defer func() {
		recover()
	}()
	panic(1)
}

// D.
func main() {
	defer func() {
		defer func() {
			recover()
		}()
	}()
	panic(1)
}
```

#### 1。答案&解析

```text
C

recover()函数必须在defer()函数中调用才有效，不支持defer中的多层函数嵌套
```

#### 2. 下面代码输出什么，请说明？

```go
package main

import "fmt"

func main() {
	defer func() {
		fmt.Println(recover())
	}()
	defer func() {
		defer fmt.Println(recover())
		panic(1)
	}()
	defer recover()
	panic(2)
}
```

#### 2. 答案&解析

```text
2 1

recover()必须在defer()函数中调用才有效。
先执行panic(2)，然后被第二个defer捕获，执行panic(1)，然后被第一个defer捕获
```
