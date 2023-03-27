#### 1. 下面这段代码输出什么？

```go
package main

import "fmt"

func (i int) PrintInt() {
	fmt.Println(i)
}

func main() {
	var i int = 1
	i.PrintInt()
}
// A. 1
// B. compilation error
```

#### 1. 答案&解析

```text
B。 基于类型创建的方法必须定义在同一包内。

解决方式：

package main

import "fmt"

type MyInt int

func (i MyInt) PrintInt() {
	fmt.Println(i)
}

func main() {
	var i MyInt = 1
	i.PrintInt()
}
```

#### 2. 下面这段代码输出什么？

```go
package main

import "fmt"

type People interface {
	Speak(string) string
}

type Student struct{}

func (stu *Student) Speak(think string) (talk string) {
	if think == "speak" {
		talk = "speak"
	} else {
		talk = "hi"
	}
	return talk
}

func main() {
	var peo People = Student{}
	think := "speak"
	fmt.Println(peo.Speak(think))
}

// A. speak
// B. compilation error
```

#### 2. 答案&解析

```text
B。

func (stu Student) Speak(think string) (talk string) {
	if think == "speak" {
		talk = "speak"
	} else {
		talk = "hi"
	}
	return talk
}
```
