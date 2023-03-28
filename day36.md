#### 1. 关于函数声明， 下面语法正确的是？

```go
// A.
func f(a, b int) (value int, err error) {return 0, nil}
// B.
func f(a int, b int) (value int, err error) {return 0, nil}
// C.
func f(a, b int) (value int, error) {return 0, nil}
// D.
func f(a int, b int) (int, int, error) {return 0, 0, nil}
```

#### 1. 答案&解析

```text
ABD

返回值要么全都不命名，要么全都命名
```

#### 2. 关于整型切片的初始化，下面正确的是？

```go
// A.
s1 := make([]int)
// B.
s2 := make([]int, 0)
// C.
s3 := make([]int, 5, 10)
// D.
s4 := []int{1, 2, 3, 4, 5}
```

#### 2. 答案&解析

```text
BCD
```

#### 3. 下面代码会触发异常吗？请说明？

```go
package main

import (
	"fmt"
	"runtime"
)

func main() {
	runtime.GOMAXPROCS(1)
	int_chan := make(chan int, 1)
	string_chan := make(chan string, 1)
	int_chan <- 1
	string_chan <- "hello"
	select {
	case value := <-int_chan:
		fmt.Println(value)
	case value := <-string_chan:
		panic(value)
	}
}
```

#### 3. 答案&解析

```text
select 会随机选择一个可用的通道做收发操作，所以说可能会触发异常。
```
