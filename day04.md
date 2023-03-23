#### 1. 下面这段代码有什么问题？

```go
package main

import "fmt"

func main() {
	list := new([]int)
	list = append(list, 1)
	fmt.Println(list)
}

```

#### 1. 答案&解析

```text
该代码无法通过编译，new([]int)之后的list是一个*[]int类型的指针， 不能对指针执行append的操作。可以使用make()初始化之后使用
```

#### 2. 下面这段代码有什么问题？

```go
package main

import "fmt"

func main() {
	s1 := []int{1, 2, 3}
	s2 := []int{4, 5}
	s1 = append(s1, s2)
	fmt.Println(s1)
}
```

#### 2. 答案&解析

```text
该代码无法通过编译。append的第二个参数不能直接用slice。需要用...操作符。
如： append(s1, s2...) append(s1, 1, 2, 3)
```

#### 3. 下面这段代码有什么问题？

```go
package main

import "fmt"

var (
	size    := 1024
	maxSize = size * 2
)

func main() {
	fmt.Println(size, maxSize)
}
```

#### 3. 答案&解析

```text
改代码无法通过编译。
简短模式声明只能在函数内部
```
