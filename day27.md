#### 1. 下面这段代码输出什么？

```go
package main

import "fmt"

type Direction int

const (
	North Direction = iota
	East
	South
	West
)

func (d Direction) String() string {
	return [...]string{"North", "East", "South", "West"}[d]
}

func main() {
	fmt.Println(East)
}

```

#### 1. 答案&解析

```text
East

如果定义了String()方法。当执行print函数时会自动使用该方法。实现字符串打印
```

#### 2. 下面代码输出什么？

```go
package main

import "fmt"

type Math struct {
	x, y int
}

var m = map[string]Math{
	"foo": {2, 3},
}

func main() {
	m["foo"].x = 4
	fmt.Println(m["foo"].x)
}
// A. 4
// B. compilation error
```

#### 2. 答案&解析

```text
编译错误

对于类型X = Y的赋值操作。必须知道X的地址。go语言中的map的value不可寻址
有两种结局方式

1. 使用临时变量
package main

import "fmt"

type Math struct {
	x, y int
}

var m = map[string]Math{
	"foo": {2, 3},
}

func main() {
	tmp := m["foo"]
	tmp.x = 4
	m["foo"] = tmp
	fmt.Println(m["foo"].x)
}

2. 修改数据结构
package main

import "fmt"

type Math struct {
	x, y int
}

var m = map[string]*Math{
	"foo": &Math{2, 3},
}

func main() {
	m["foo"].x = 4
	fmt.Println(m["foo"].x)
}
```