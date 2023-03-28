#### 1. 下面的代码有什么问题？

```go
package main

import "fmt"

type X struct{}

func (x *X) test() {
	fmt.Println(x)
}

func main() {
	var a *X
	a.test()
	X{}.test()
}
```

#### 1. 答案&解析

```text
X{}是不可寻址的，不能直接调用方法。
可修复为：
package main

import "fmt"

type X struct{}

func (x *X) test() {
	fmt.Println(x)
}

func main() {
	var a *X
	a.test()
	var x = X{}
	x.test()
}
```

#### 2. 下面代码有什么不规范的地方？

```go
package main

import "fmt"

func main() {
	x := map[string]string{"one": "a", "two": "b", "three": "c"}
	if v := x["two"]; v == "" {
		fmt.Println("no entry")
	}
}
```

#### 2. 答案&解析

```text
标准写法：
package main

import "fmt"

func main() {
	x := map[string]string{"one": "a", "two": "b", "three": "c"}
	if _, ok := x["tow"]; !ok {
		fmt.Printf("no entry")
	}
}
```
