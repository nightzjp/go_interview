#### 1. 定义一个包含全局字符串的变量，下面语法正确的是？

```go
// A. var str string
// B. str := ""
// C. str = ""
// D. var str = ""
```

#### 1. 答案&解析

```text
AD。

var 可定义全局变量。变量类型可不写自行推导
```

#### 2. 下面这段代码输出什么？

```go
package main

import "fmt"

func hello(i int) {
	fmt.Println(i)
}

func main() {
	i := 5
	defer hello(i)
	i += 10
}
```

#### 2. 答案&解析

```text
5。

hello函数的参数在执行defer语句的时候会保存一份副本
```

#### 3. 下面这段代码输出什么？

```go
package main

import "fmt"

type People struct{}

func (p *People) ShowA() {
	fmt.Println("showA")
	p.ShowB()
}

func (p *People) ShowB() {
	fmt.Println("showB")
}

type Teacher struct {
	People
}

func (t *Teacher) ShowB() {
	fmt.Println("teacher showB")
}

func main() {
	t := Teacher{}
	t.ShowA()
}
```

#### 3. 答案&解析

```text
showA
showB

Teacher没有自己的ShowA，所以调用内部类型People的同名方法，People->showA方法调用自己的ShowB方法。
```
