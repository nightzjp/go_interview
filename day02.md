#### 1. 下面的代码输出什么？

```go
package main

import "fmt"

func main() {
	slice := []int{0, 1, 2, 3}
	m := make(map[int]*int)

	for key, val := range slice {
		m[key] = &val
	}
	for k, v := range m {
		fmt.Println(k, "->", *v)
	}
}
```

#### 1. 答案&解析

```text
0 -> 3
1 -> 3
2 -> 3
3 -> 3

for range循环的时候会创建每个元素的副本，而不是元素的引用，所以m[key] = &val取的都是变量val的地址，所以最后map中的所有元素都是变量val的地址，因为最后val被赋值为3，所以所有的输出都是3
```

#### 1. 修正后的写法

```go
package main

import "fmt"

func main() {
	slice := []int{0, 1, 2, 3}
	m := make(map[int]*int)

	for key, val := range slice {
		value := val
		m[key] = &value
	}
	for k, v := range m {
		fmt.Println(k, "->", *v)
	}
}
```
