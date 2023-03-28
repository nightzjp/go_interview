#### 1. 下面代码有什么问题？

```go
package main

import (
	"fmt"
	"log",
	"time"
)

func main() {
}
```

#### 1. 答案&解析

```text
导入的包如果没有被使用会报编译错误

代码可以修复为：
package main

import (
	_ "fmt"
	"log",
	"time"
)

var _ = log.Println

func main() {
    _ = time.Now
}
```

#### 2. 下面代码输出什么？

```go
package main

import "fmt"

func main() {
	x := interface{}(nil)
	y := (*int)(nil)
	a := y == x
	b := y == nil
	_, c := x.(interface{})
	fmt.Println(a, b, c)
}

// A. true true false
// B. false true true
// C. true true true
// D. false true false
```

#### 2. 答案&解析

```text
D.

i.(Type),其中i是接口。Type是类型或接口。编译时会自动检测i的动态类型是否与Type一致。如果类型不存在则断言失败
```

#### 3. 下面的代码有什么问题？

```go
package main

func main() {
	var s []int
	s = append(s, 1)
	var m map[string]int
	m["one"] = 1
}
```

#### 3. 答案&解析

```text
不能对nil的map直接赋值。需要使用map进行初始化；可以使用append对nil的slice增加元素

修复代码：
package main

func main() {
	var s []int
	s = append(s, 1)
	var m map[string]int
	m = make(map[string]int)
	m["one"] = 1
}
```
