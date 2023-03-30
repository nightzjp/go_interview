#### 1. 下面这段代码能通过编译吗？

```go
package main

import "fmt"

func main() {
	m := make(map[string]int)
	m["foo"]++
	fmt.Println(m["foo"])
}
```

#### 1. 答案&解析

```text
能编译通过。上述代码可理解为：
package main

import "fmt"

func main() {
	m := make(map[string]int)
	v := m["foo"]
	v++
	m["foo"] = v
	fmt.Println(m["foo"])
}
```

#### 2. 下面的代码输出什么？

```go
package main

import (
	"fmt"
	"os"
)

func Foo() error {
	var err *os.PathError = nil
	return err
}

func main() {
	err := Foo()
	fmt.Println(err)
	fmt.Println(err == nil)
}
```

#### 2. 答案&解析

```text
nil false

接口值与nil值，只有在值和动态类型都为nil的情况下，接口值才为nil， Foo()函数返回的err变量，值为nil，动态类型为*os.PathError
可修复为:
package main

import (
	"fmt"
)

func Foo() (err error) {
	return err
}

func main() {
	err := Foo()
	fmt.Println(err)
	fmt.Println(err == nil)
}
```
