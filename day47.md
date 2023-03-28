#### 1. 下面的代码有什么问题？

```go
package main

import "fmt"

func main() {
	data := []int{1,2,3}
	i := 0
	++i
	fmt.Println(data[i++])
}
```

#### 1. 答案&解析

```text
go语言中不支持++i,--i等操作
表达式可以作为语句使用，但语句不能当做表达式
```

#### 2. 下面代码最后一行输出什么？

```go
package main

import "fmt"

func main() {
	x := 1
	fmt.Println(x)
	{
		fmt.Println(x)
		i, x := 2, 2
		fmt.Println(i, x)
	}
	fmt.Println(x)
}
```

#### 2. 答案&解析

```text
1

代码作用域
```
