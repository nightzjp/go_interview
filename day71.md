#### 1. 判断题

```go
// 对变量x的去翻操作是~x?
```

#### 1. 答案&解析

```text
错

go语言的取反操作是^，它返回一个每个bit位都取反的数。
```

#### 2. 下面代码输出什么？请简要说明

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
	defer s.Add(1).Add(2)
	s.Add(3)
}
```

#### 2. 答案&解析

```text
1 3 2

Add()方法的返回值是指针类型*Slice，所以可以链式调用
```
