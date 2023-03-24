#### 1.关于cap()函数的适用类型，下面说法正确的是？

```go
// A. array
// B. slice
// C. map
// D. channel
```

#### 1. 答案&解析

```text
ABD。

cap()函数不适用map
```

#### 2. 下面这段代码输出什么？

```go
package main

import "fmt"

func main() {
	var i interface{}
	if i == nil {
		fmt.Println("nil")
		return
	}
	fmt.Println("not nil")
}

// A. nil
// B. not nil
// C. compilation error
```

#### 2. 答案&解析

```text
A。

当接口的动态类型和值类型都为nil时，接口类型值为nil
```

#### 3. 下面这段代码输出什么？

```go
package main

import "fmt"

func main() {
	s := make(map[string]int)
	delete(s, "h")
	fmt.Println(s["h"])
}

// A. runtime panic
// B. 0
// C. compilation error
```

#### 3. 答案&解析

```text
B。

删除map不存在的键值对时，不会报错。获取不存在的键值对时，返回值类型所对应的零值
```
