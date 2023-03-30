#### 1. 下面代码能编译通过吗？

```go
package main

import "fmt"

func main() {
	true := false
	fmt.Println(true)
}
```

#### 1. 答案&解析

```text
编译通过。不建议这么做
```

#### 2. 下面的代码输出什么？

```go
package main

import "fmt"

func watShadowDefer(i int) (ret int) {
	ret = i * 2
	if ret > 10 {
		ret := 10
		defer func() {
			ret = ret + 1
		}()
	}
	return
}

func main() {
	result := watShadowDefer(50)
	fmt.Println(result)
}
```

#### 2. 答案&解析

```text
100 变量作用域和defer返回值
```
