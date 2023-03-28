#### 1. 关于类型转化，下面选项正确的是？

```go
// A.
type MyInt int
var i int = 1
var j MyInt = i

// B.
type MyInt int
var i int = 1
var j MyInt = (MyInt)i

// C.
type MyInt int
var i int = 1
var j MyInt = MyInt(i)

// D. 
type MyInt int
var i int = 1
var j MyInt = i.(MyInt)
```

#### 1. 答案&解析

```text
C

强制类型转化
```

#### 2. 关于switch语句，下面说法正确的有？

```go
// A. 条件表达式必须为常量或整数
// B. 单个case中，可以出现多个结果选项
// C. 需要用break来明确退出一个case
// D. 只有在case中明确添加fallthrough关键字，才会继续执行紧跟的下一个case
```

#### 2. 答案&解析

```text
BD
```

#### 3. 如果Add()函数的调用代码如下所示，那么Add函数定义正确的是？

```go
package main

import "fmt"

func main() {
	var a Integer = 1
	var b Integer = 2
	var i interface{} = &a
	sum := i.(*Integer).Add(b)
	fmt.Println(sum)
}

// A.
type Integer int

func (a Integer) Add(b Integer) Integer {
	return a + b
}

// B.
type Integer int

func (a Integer) Add(b *Integer) Integer {
	return a + *b
}

// C.
type Integer int

func (a *Integer) Add(b Integer) Integer {
	return *a + b
}

// D.
type Integer int

func (a *Integer) Add(b *Integer) Integer {
	return *a + *b
}
```

#### 3. 答案&解析

```text
AC

类型断言，方法集
```
