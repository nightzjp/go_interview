#### 1. 关于channel的特性，下面说法正确的是？

```go
// A. 给一个nil channel发送数据，造成永远堵塞
// B. 从一个nil channel接收数据，造成永远堵塞
// C. 给一个已经关闭的channel发送数据，引发panic
// D. 从一个已经关闭的channel接收数据，如果缓冲区为空，返回一个零值
```

#### 1. 答案&解析

```text
ABCD
```

#### 2. 下面代码有什么问题？

```go
package main

import "fmt"

const i = 100

var j = 123

func main() {
	fmt.Println(&j, j)
	fmt.Println(&i, i)
}
```

#### 2. 答案&解析

```text
编译报错。常量不会分配内存空间，无法寻址
```

#### 3. 下面代码能否编译通过？如果通过输出什么？

```go
package main

import "fmt"

func GetValue(m map[int]string, id int) (string, bool) {
	if _, exist := m[id]; exist {
		return "exist", true
	}
	return nil, false
}

func main() {
	intmap := map[int]string{
		1: "a",
		2: "b",
		3: "c",
	}
	v, err := GetValue(intmap, 3)
	fmt.Println(v, err)
}

```

#### 3. 答案&解析

```text
不能编译通过。
nil不可作为string类型的零值
```
