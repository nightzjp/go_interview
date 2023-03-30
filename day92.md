#### 1. 下面代码输出什么？

```go
package main

import "fmt"

var x int

func init() {
	x++
}

func main() {
	init()
	fmt.Println(x)
}
```

#### 1. 答案&解析

```text
编译失败。

init()函数不能被其它函数调用
```

#### 2. main()函数是求两个数之间的较小值，能否在该函数中添加一行代码将其功能补全。

```go
package main

import "fmt"

func min(a int, b uint) {
	var min = 0
	fmt.Printf("the min of %d and %d is %d", a, b, min)
}

func main() {
	min(1225, 256)
}
```

#### 2. 答案&解析

```text
利用copy()函数的功能，切片复制，并且返回两者长度的较小值
package main

import "fmt"

func min(a int, b uint) {
	var min = 0
	min = copy(make([]struct{}, a), make([]struct{}, b))
	fmt.Printf("the min of %d and %d is %d", a, b, min)
}

func main() {
	min(1225, 256)
}
```
