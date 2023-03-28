#### 1. 下面这段代码有什么问题？

```go
package main

import "fmt"

var gvar int

func main() {
	var one int
	two := 2
	var three int
	three = 3
	func(unused string) {
		fmt.Println("Unused arg. No compile error")
	}("what?")
}
```

#### 1. 答案&解析

```text
变量声明未使用

可以移除或注释未使用的变量
```

#### 2. 下面代码输出什么？

```go
package main

import "fmt"

type ConfigOne struct {
	Daemon string
}

func (c *ConfigOne) String() string {
	return fmt.Sprintf("print: %v", c)
}

func main() {
	c := &ConfigOne{}
	_ = c.String()
}
```

#### 2. 答案&解析

```text
运行错误

如果类型实现了String()方法，当格式化输出的时候会自动使用String()方法。在内部使用格式化输出会造成递归调用。最后抛错
```

#### 3. 下面代码输出什么？

```go
package main

import "fmt"

func main() {
	var a = []int{1, 2, 3, 4, 5}
	var r = make([]int, 0)
	for i, v := range a {
		if i == 0 {
			a = append(a, 6, 7)
		}
		r = append(r, v)
	}
	fmt.Println(r)
}
```

#### 3. 答案&解析

```text
[1 2 3 4 5]

for range 循环采用副本循环
```
