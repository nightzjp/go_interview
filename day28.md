#### 1. 下面的代码有什么问题？

```go
package main

import "fmt"

func main() {
	fmt.Println([...]int{1} == [2]int{1})
	fmt.Println([]int{1} == []int{1})
}
```

#### 1. 答案&解析

```text
go语言中不同类型不可以比较
切片不可以比较
```

#### 2. 下面代码输出什么？

```go
package main

import "fmt"

var p *int

func foo() (*int, error) {
	var i int = 5
	return &i, nil
}

func bar() {
	fmt.Println(*p)
}

func main() {
	p, err := foo()
	if err != nil {
		fmt.Println(err)
		return
	}
	bar()
	fmt.Println(*p)
}
// A. 5 5
// B. runtime error
```

#### 2. 答案&解析

```text
B.

变量作用域
可修改为：
package main

import "fmt"

var p *int

func foo() (*int, error) {
	var i int = 5
	return &i, nil
}

func bar() {
	fmt.Println(*p)
}

func main() {
	var err error
	p, err = foo()
	if err != nil {
		fmt.Println(err)
		return
	}
	bar()
	fmt.Println(*p)
}
```
