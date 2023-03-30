#### 1. 下面代码输出什么？

```go
package main

import "fmt"

func main() {
	a := 1
	for i := 0; i < 5; i++ {
		a := a + 1
		a = a * 2
	}
	fmt.Println(a)
}
```

#### 1. 答案&解析

```text
1. 
变量的作用域

for语句的变量a是重新声明，它的作用域仅在for语句范围内
```

#### 2. 下面的代码输出什么？

```go
package main

import "fmt"

func test(i int) (ret int) {
	ret = i * 2
	if ret > 10 {
		ret := 10
		return
	}
	return
}

func main() {
	result := test(10)
	fmt.Println(result)
}
```

#### 2. 答案&解析

```text
编译错误。变量作用域
```
