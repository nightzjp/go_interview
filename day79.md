#### 1. interface{}是可以指向任意对象的Any类型，是否正确？

```go
// A. false
// B. true
```

#### 1. 答案&解析

```text
B
```

#### 2. 下面的代码有什么问题？

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
	c.String()
}
```

#### 2. 答案&解析

```text
无线递归栈溢出。

如果类型定义了String()方法，在使用Printf(), Print(), SprintF()等格式化输出是会自动使用String()方法。
```
