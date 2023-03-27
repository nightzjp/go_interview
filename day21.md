#### 1. 下面的两个切片声明有什么区别？

```go
// var a []int
// a := []int{}
```

#### 1. 答案&解析

```text
A 声明的是nil切片；B声明的是长度和容量都为0的空切片。
A声明方式不会分配内存，优先选择
```

#### 2. A、B、C、D那些选项语法错误？

```go
package main

type S struct {}

func f(x interface{})  {}

func g(x *interface{})  {}

func main() {
	s := S{}
	p := &s
	f(s)  // A
	g(s)  // B
	f(p)  // C
	g(p)  // D
}
```

#### 2. 答案&解析

```text
BD

函数参数为interface{}时可以接收任何类型的参数，包括用户自定义的类型等，即使接收的是指针类型也应该用interface{}，而不是*interface{}
```

#### 3. 下面A、B两个地方应该填入什么代码，才能顺利的打印出结果？

```go
package main

import "fmt"

type S struct {
	m string
}

func f() *S {
	return _  // A
}

func main() {
	p := _  // B
	fmt.Println(p.m)  // print "foo"
}
```

#### 3. 答案&解析

```text
A. &S{"foo"}
B. f()

f()函数返回参数是指针类型，所以可以采用&取结构体的指针。
```
