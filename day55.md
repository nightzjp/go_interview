#### 1. 关于channel，下面描述正确的是？

```go
// A. close()可以用于只接收通道
// B. 单向通道可以转换为双向通道
// C. 不能在单向通道上做逆向操作
```

#### 1. 答案&解析

```text
C
```

#### 2. 下面的代码有什么问题？

```go
package main

type T struct {
	n int
}

func getT() T {
	return T{}
}

func main() {
	getT().n = 1
}
```

#### 2. 答案&解析

```text
T{}无法寻址，不可直接赋值。
代码可修复为：
package main

import "fmt"

type T struct {
	n int
}

func getT() T {
	return T{}
}

func main() {
	t := getT()
	p := &t.n
	*p = 1
	fmt.Println(t.n)
}
```
