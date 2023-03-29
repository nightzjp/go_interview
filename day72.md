#### 1. 下面的代码输出什么，请说明？

```go
package main

import "fmt"

type Slice []int

func NewSlice() Slice {
	return make(Slice, 0)
}

func (s *Slice) Add(elem int) *Slice {
	*s = append(*s, elem)
	fmt.Println(elem)
	return s
}

func main() {
	s := NewSlice()
	defer func() {
		s.Add(1).Add(2)
	}()
	s.Add(3)
}
```

#### 1. 答案&解析

```text
3 1 2
```

#### 2. 下面的代码输出什么，请说明。

```go
package main

import "fmt"

type Orange struct {
	Quantity int
}

func (o *Orange) Increase(n int) {
	o.Quantity += n
}

func (o *Orange) Decrease(n int) {
	o.Quantity -= n
}

func (o *Orange) String() string {
	return fmt.Sprintf("%#v", o.Quantity)
}

func main() {
	var orange Orange
	orange.Increase(10)
	orange.Decrease(5)
	fmt.Println(orange)
}
```

#### 2. 答案&解析

```text
{5}

String()是指针方法，而不是值方法，所以使用Print不会调用。
可以修复为：
func main() {
	orange := &Orange{}
	orange.Increase(10)
	orange.Decrease(5)
	fmt.Println(orange)
}
```
