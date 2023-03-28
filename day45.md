#### 1. 下面代码有什么问题？

```go
package main

import "fmt"

func main() {
	one := 0
	one := 1
	fmt.Println(one)
}
```

#### 1. 答案&解析

```text
变量重复声明。

修复代码：
package main

import "fmt"

func main() {
	one := 0
	one, two := 1, 2
	fmt.Println(one, two)
	one, two = two, one
	fmt.Println(one, two)
}
```

#### 2. 下面代码有什么问题？

```go
package main

func main() {
	x := []int{
		1,
		2
	}
	_ = x
}
```

#### 2. 答案&解析

```text
用字面量初始化数组、slice和map的时候，最好在每个元素后边加上逗号
```

#### 3. 下面代码输出什么？

```go
package main

import "fmt"

func test(x byte) {
	fmt.Println(x)
}

func main() {
	var a byte = 0x11
	var b uint8 = a
	var c uint8 = a + b
	test(c)
}
```

#### 3. 答案&解析

```text
34

byte是uint8的别名；rune是int32的别名
```
