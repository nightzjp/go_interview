#### 1. 下面那一行代码会引发panic，说明原因

```go
package main

func main() {
	var x interface{}
	var y interface{} = []int{3, 5}
	_ = x == x
	_ = x == y
	_ = y == y
}
```

#### 1. 答案&解析

```text
第八行： _ = y == y
两个比较值的动态类型为同一个不可比较类型
```

#### 2. 下面的代码输出什么？

```go
package main

import "fmt"

var o = fmt.Print

func main() {
	c := make(chan int, 1)
	for range [3]struct{}{} {
		select {
		default:
			o(1)
		case <-c:
			o(2)
			c = nil
		case c <- 1:
			o(3)
		}
	}
}
```

#### 2. 答案&解析

```text
321

第一次循环，写操作已经准备好，执行o(3)，输出3
第二次循环，读操作已经准备好，执行o(2)，输出2并将c赋值为nil
第三次循环，由于c为nil，走默认default分支输出1
```
