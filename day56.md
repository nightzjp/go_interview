#### 1. 下面的代码有什么问题？

```go
package main

import "fmt"

func main() {
	s := make([]int, 3, 9)
	fmt.Println(len(s))
	s2 := s[4:8]
	fmt.Println(len(s2))
}
```

#### 1. 答案&解析

```text
3 [0 0 0]
4 [0 0 0 0]
```

#### 2. 下面代码输出什么？

```go
package main

import "fmt"

type N int

func (n N) test() {
	fmt.Println(n)
}

func main() {
	var n N = 10
	p := &n
	n++
	f1 := p.test
	n++
	f2 := p.test
	n++
	fmt.Println(n)
	f1()
	f2()
}
```

#### 2. 答案&解析

```text
13 11 12

当指针赋值给变量或者作为函数参数传递时，会立即计算并复制该方法执行所需的接受者对象，与其绑定，以便后续执行
```
