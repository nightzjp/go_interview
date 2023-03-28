#### 1. 下面代码编译能通过吗？

```go
func main() 
{
	fmt.Println("hello world.")
}
```

#### 1. 答案&解析

```text
语法错误！

go语言中，大括号不能单独放一行。
```

#### 2. 下面这段代码输出什么？

```go
package main

import "fmt"

var x = []int{2: 2, 3, 0: 1}

func main() {
	fmt.Println(x)
}
```

#### 2. 答案&解析

```text
[1 0 2 3]

切片指定索引初始化
```

#### 3. 下面这段代码输出什么？

```go
package main

import "fmt"

func incr(p *int) int {
	*p++
	return *p
}

func main() {
	v := 1
	incr(&v)
	fmt.Println(v)
}
```

#### 3. 答案&解析

```text
2.

指针。指针变量
```
