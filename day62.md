#### 1. 下面哪一行代码会编译报错，请说明。

```go
package main

import "fmt"

func main() {
	nil := 123
	fmt.Println(nil)
	var _ map[string]int = nil
}
```

#### 1. 答案&解析

```text
第8行

当前作用域中，预定义的nil被覆盖，此时nil为int类型，不能赋值给map类型
```

#### 2. 下面代码输出什么？

```go
package main

import "fmt"

func main() {
	var x int8 = -128
	var y = x / -1
	fmt.Println(y)
}
```

#### 2. 答案&解析

```text
-128

溢出
```
