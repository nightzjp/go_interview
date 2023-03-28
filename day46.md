#### 1. 下面代码有什么问题？

```go
package main

import "fmt"

func main() {
	const x = 123
	const y = 1.23
	fmt.Println(x)
}
```

#### 1. 答案&解析

```text
常量声明未使用可以编译通过
```

#### 2. 下面代码输出什么？

```go
package main

import "fmt"

const (
	x uint16 = 120
	y
	s = "abc"
	z
)

func main() {
	fmt.Printf("%T %v\n", y, y)
	fmt.Printf("%T %v\n", z, z)
}
```

#### 2. 答案&解析

```text
uint16 120
string abc

常量组中如果不指定类型和初始化值，则与上一行非空常量右值相同
```

#### 3. 下面代码有什么问题？

```go
package main

func main() {
	var x string = nil
	if x == nil {
		x = "default"
	}
}
```

#### 3. 答案&解析

```text
nil不可作为string的零值。字符串的零值为""
```
