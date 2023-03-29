#### 1. flag是bool型变量，下面if表达式符合编码规范的是？

```go
// A. if flag == 1
// B. if flag
// C. if flag == false
// D. if !flag
```

#### 1. 答案&解析

```text
BCD

bool类型跟整型无法比较
```

#### 2. 下面的代码输出什么，请说明？

```go
package main

import "fmt"

func main() {
	defer func() {
		fmt.Println(recover())
	}()
	defer func() {
		defer func() {
			fmt.Println(recover())
		}()
		panic(1)
	}()
	defer recover()
	panic(2)
}
```

#### 2. 答案&解析

```text
1 2
```
