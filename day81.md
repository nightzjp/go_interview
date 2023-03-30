#### 1. 下面的代码输出什么？

```go
package main

import "fmt"

func main() {
	var a []int = nil
	a, a[0] = []int{1, 2}, 9
	fmt.Println(a)
}
```

#### 1. 答案&解析

```text
编译错误。多重赋值
```

#### 2. 下面代码中的指针p为野指针，因为返回的栈内存在函数结束时会被释放？

```go
package main

import "fmt"

type TimesMatcher struct {
	base int
}

func NewTimesMatcher(base int) *TimesMatcher {
	return &TimesMatcher{base: base}
}

func main() {
	p := NewTimesMatcher(3)
	fmt.Println(p)
}

// A. false
// B. true
```

#### 2. 答案&解析

```text
A

go语言内存回收机制规定，只要有一个指针指向引用一个变量，那么这个变量就不会被释放(内存逃逸),因此在go语言中返回函数或临时变量是安全的。
```
