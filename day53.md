#### 1. 关于channel下面描述正确的是？

```go
// A. 向已关闭的通道发送数据会引发panic
// B. 从已关闭的缓冲通道接收数据，返回以缓冲数据或零值
// C. 无论接收还是发送，nil通道都会阻塞
```

#### 1. 答案&解析

```text
ABC
```

#### 2. 下面的代码有什么问题？

```go
package main

type T struct {
	n int
}

func (t *T) Set(n int) {
	t.n = n
}

func getT() T {
	return T{}
}

func main() {
	getT().Set(1)
}
```

#### 2. 答案&解析

```text
1. 直接返回的T{}不可寻址
2. 不可寻址的结构体不能调用带结构体指针接收者的方法

可修复代码为：
package main

import "fmt"

type T struct {
	n int
}

func (t *T) Set(n int) {
	t.n = n
}

func getT() T {
	return T{}
}

func main() {
	t := getT()
	t.Set(2)
	fmt.Println(t.n)
}
```
