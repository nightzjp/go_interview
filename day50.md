#### 1. 下面这段代码输出什么？

```go
package main

import "fmt"

type T struct {
	ls []int
}

func foo(t T) {
	t.ls[0] = 100
}

func main() {
	var t = T{
		ls: []int{1, 2, 3},
	}
	foo(t)
	fmt.Println(t.ls[0])
}

// A. 1
// B. 100
// C. compilation error
```

#### 1. 答案&解析

```text
B

调用foo()函数是虽然是传值，但是在函数中。字段ls依旧可以看做指向底层数组的指针
```

#### 2. 下面代码输出什么？

```go
package main

import "fmt"

func main() {
	isMatch := func(i int) bool {
		switch i {
		case 1:
		case 2:
			return true
		}
		return false
	}
	fmt.Println(isMatch(1))
	fmt.Println(isMatch(2))
}
```

#### 2. 答案&解析

```text
false true

go语言switch-case语句自带break；可以通过添加fallthrough语句强制执行下一个case
```
