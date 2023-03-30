#### 1. 关于cap函数适用于下列那些类型？

```go
// A. array
// B. channel
// C. map
// D. slice
```

#### 1. 答案&解析

```text
ABD

array返回数组的元素个数
slice返回slice的最大容量
channel返回channel的容量
```

#### 2. 下面代码输出什么？

```go
package main

import (
	"fmt"
	"testing"
)

func hello(num ...int) {
	num[0] = 18
}

func Test13(t *testing.T) {
	i := []int{5, 6, 7}
	hello(i...)
	fmt.Println(i[0])
}

func main() {
	t := &testing.T{}
	Test13(t)
}

// A. 18
// B. 5
// C. compilation error
```

#### 2. 答案&解析

```text
A 

可变函数是指针传递
```
