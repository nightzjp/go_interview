#### 1. 关于map，下面说法正确的是？

```go
// A. map反序列化时，json.unmarshal()的入参必须为map的地址
// B. 在函数中调用传递map，则子函数中对map元素的增加不会导致父函数中map的修改
// C. 在函数调用中传递map，则子函数中对map元素的修改不会导致父函数中map的修改
// D. 不能使用内置函数delete()删除map的元素
```

#### 1. 答案&解析

```text
A
```

#### 2. 下面代码输出什么？请简要说明

```go
package main

import "fmt"

type Foo struct {
	val int
}

func (f Foo) Inc(inc int) {
	f.val += inc
}

func main() {
	var f Foo
	f.Inc(100)
	fmt.Println(f.val)
}
```

#### 2. 答案&解析

```text
0

使用值类型接受者定义的方法，调用的时候，使用的是值的副本，对副本操作不会影响原来的值，如果需要影响，请使用指针接受者
修复为：

package main

import "fmt"

type Foo struct {
	val int
}

func (f *Foo) Inc(inc int) {
	f.val += inc
}

func main() {
	f := &Foo{}
	f.Inc(100)
	fmt.Println(f.val)
}
```
