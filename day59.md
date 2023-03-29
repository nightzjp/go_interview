#### 1. 下面的代码输出什么？

```go
package main

import "fmt"

type N int

func (n *N) test() {
	fmt.Print(*n)
}

func main() {
	var n N = 10
	p := &n

	n++
	f1 := p.test

	n++
	f2 := p.test

	n++
	fmt.Print(n)

	f1()
	f2()
}
```

#### 1. 答案&输出

```text
13 13 13

参考第56天。当目标方法的接受者是指针类型的时候。被复制的是指针。
```

#### 2. 下面哪一行代码会引发panic，请说明

```go
package main

func main() {
	var m map[int]bool
	_ = m[123]
	var p *[5]string
	for range p {
		_ = len(p)
	}
	var s []int
	_ = s[:]
	s, s[0] = []int{1, 2}, 9
}
```

#### 2. 答案&解析

```text
第12行

nil切片赋值
```