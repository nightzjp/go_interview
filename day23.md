#### 1. 下面这段代码输出什么？为什么？

```go
package main

import "fmt"

func main() {
	s1 := []int{1, 2, 3}
	s2 := s1[1:]
	s2[1] = 4
	fmt.Println(s1)
	s2 = append(s2, 5, 6, 7)
	fmt.Println(s1)
}
```

#### 1. 答案&解析

```text
[1 2 4]
[1 2 4]

golang中切片底层的数据结构是数组。当使用s1[1:]获得切片s2，和s1共享一个底层数组。所以s2[1] = 4将会修改s1.
而append操作会导致底层数组扩容，生成新的数组。因此追加数据后的s2不会影响s1。
为什么修改s2的第一个元素影响s1的第二个元素：s2索引为1的元素对应s1索引为2的元素
```

#### 2. 下面选项正确的是？

```go
package main

import "fmt"

func main() {
	if a := 1; false {
	} else if b := 2; false {
	} else {
		fmt.Println(a, b)
	}
}
// A. 1 2
// B. compilation error
```

#### 2. 答案&解析

```text
A.

代码块和变量的作用域
```
