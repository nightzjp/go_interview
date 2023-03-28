#### 1. 下面的代码有什么问题？

```go
package main

import "fmt"

type N int

func (n N) value() {
	n++
	fmt.Printf("v:%p,%v\n", &n, n)
}

func (n *N) pointer() {
	*n++
	fmt.Printf("v:%p,%v\n", &n, n)
}

func main() {
	var a N = 25
	p := &a
	p1 := &p
	p1.value()
	p1.pointer()
}
```

#### 1. 答案&解析

```text
不能使用多级指针调用方法
```

#### 2. 下面的代码输出什么？

```go
package main

import "fmt"

type N int

func (n N) test() {
	fmt.Println(n)
}

func main() {
	var n N = 10
	fmt.Println(n)

	n++
	f1 := N.test
	f1(n)

	n++
	f2 := (*N).test
	f2(&n)
}
```

#### 2. 答案&解析

```text
10 11 12

通过类型引用的方法表达式会被还原成普通函数的样式，接受者的第一个参数调用时显示传参。类型可以是T或*T，只要目标方法存在于该类型的方法集中就可以
还可以直接使用方法表达式调用：
package main

import "fmt"

type N int

func (n N) test() {
	fmt.Println(n)
}

func main() {
	var n N = 10
	fmt.Println(n)

	n++
	N.test(n)

	n++
	(*N).test(&n)
}
```
