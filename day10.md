#### 1. 下面这段代码输出什么？

```go
package main

import "fmt"

func main() {
	a := 5
	b := 8.1
	fmt.Println(a + b)
}
// A. 13.1
// B. 13
// C. compilation error
```

#### 1. 答案&解析

```text
C。

两个不同数据类型的数据不能相加，编译报错
```

#### 2. 下面这段代码输出什么？

```go
package main

import "fmt"

func main() {
	a := [5]int{1, 2, 3, 4, 5}
	t := a[3:4:4]
	fmt.Println(t[0])
}

// A. 3
// B. 4
// C. compilation error
```

#### 2. 答案&解析

```text
B。

[i:j:k]
假设底层数据的大小为k，截取之后的切片长度和容量分别为：j-i, k-i
```

#### 3. 下面这段代码输出什么？

```go
package main

import "fmt"

func main() {
	a := [2]int{5, 6}
	b := [3]int{5, 6}
	if a == b {
		fmt.Println("equal")
	} else {
		fmt.Println("not equal")
	}
}

// A. compilation error
// B. equal
// C. not equal
```

#### 3. 答案&解析

```text
A。

不同的类型不能进行比较
```
