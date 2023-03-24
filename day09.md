#### 1. 关于channel，下面语法正确的是？

```go
// A. var ch chan int
// B. ch := make(chan int)
// C. <-ch
// D. ch <-
```

#### 1. 答案&解析

```text
ABC。

A为声明一个channel，B为初始化一个channel
读取channel可以无接收值，写channel都必须带上值
```

#### 2. 下面这段代码输出什么？

```go
package main

import "fmt"

type person struct {
	name string
}

func main() {
	var m map[person]int
	p := person{"zjp"}
	fmt.Println(m[p])
}
// A. 0
// B. 1
// C. compilation error
```

#### 2. 答案&解析

```text
A。

打印一个map不存在的值时，返回该元素的零值。
```

#### 3. 下面这段代码输出什么？

```go
package main

import "fmt"

func hello(num ...int) {
	num[0] = 18
}

func main() {
	i := []int{5, 6, 7}
	hello(i...)
	fmt.Println(i[0])
}

// A. 18
// B. 5
// C. compilation error
```

#### 3. 答案&解析

```text
A。

函数可变参数传递
```
