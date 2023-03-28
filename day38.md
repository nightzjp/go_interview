#### 1. 关于异常的触发，下面说法正确的是？

```go
// A. 空指针解析
// B. 下标越界
// C. 除数为0
// D. 调用panic函数
```

#### 1. 答案&解析

```text
ABCD
```

#### 2. 下面代码输出什么？

```go
package main

import "fmt"

func main() {
	x := []string{"a", "b", "c"}
	for v := range x {
		fmt.Println(v)
	}
}
```

#### 2. 答案&解析

```text
0 1 2
输出索引值
```

#### 3. 下面这段代码能否编译通过？如果通过输出什么？

```go
package main

import "fmt"

type User struct{}
type User1 User
type User2 = User

func (u User1) m1() {
	fmt.Println("m1")
}

func (u User) m2() {
	fmt.Println("m2")
}

func main() {
	var i1 User1
	var i2 User2
	i1.m1()
	i2.m2()
}
```

#### 3. 答案&解析

```text
m1 m2

User1为User类型
User2为User别名
```
