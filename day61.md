#### 1. 下面这段代码输出什么？

```go
package main

import "fmt"

func main() {
	var k = 1
	var s = []int{1, 2}
	k, s[k] = 0, 3
	fmt.Println(s[0] + s[1])
}
```

#### 1. 答案&解析

```text
4

多重赋值分为2个步骤，有先后顺序
计算等号左边的索引表达式和取址表达式，接着计算等号右边的表达式
```

#### 2. 下面代码输出什么？

```go
package main

import "fmt"

func main() {
	var k = 9
	for k = range []int{} {
	}
	fmt.Println(k)
	for k = 0; k < 3; k++ {
	}
	fmt.Println(k)
	for k = range (*[3]int)(nil) {
	}
	fmt.Println(k)
}
```

#### 2. 答案&解析

```text
9 3 2
```
