#### 1. 下面的代码输出什么？

```go
package main

import "fmt"

func main() {
	// s1
	s1 := make([]int, 5)
	s1 = append(s1, 1, 2, 3)
	fmt.Println(s1)

	// s2
	s2 := make([]int, 0)
	s2 = append(s2, 1, 2, 3, 4)
	fmt.Println(s2)
}
```

#### 1. 答案&解析

```text
[0 0 0 0 0 1 2 3]
[1 2 3 4]

s1的初始化切片为: [0 0 0 0 0] append之后为[0 0 0 0 0 1 2 3]
s2的初始化切片为: [] append之后为[1 2 3 4]
```

#### 2. 下面这段代码有什么缺陷？

```go
package main

func funcMui(x, y int) (sum int, error) {
	return x + y, nil
}
```

#### 2. 答案&解析

```text
函数第二个返回值没有命名

在函数有多个返回值的情况下，只要有一个返回值命名，其他的返回值必须命名
```

#### 3. new() 与 make()的区别

```text
new(T)和make(T, args)是go语言的内建函数，用来分配内存，但是适用的类型不同。

new(T)会为T类型的新值分配已置零的内存空间，并返回地址，即*T的值。可用于array，struct等。
make(T, args)返回初始化之后的T类型的引用。可用于slice、map和channel
```
