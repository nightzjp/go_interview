#### 1. 下面代码的输出是什么？

```go
package main

import "fmt"

func main() {
	defer func() { fmt.Println("in.") }()
	deferCall()
	defer func() { fmt.Println("out.") }()
	
}

func deferCall() {
	defer func() { fmt.Println("打印前") }()
	defer func() { fmt.Println("打印中") }()
	defer func() { fmt.Println("打印后") }()
	panic("触发异常")
}
```

#### 1. 答案&解析

```text
执行结果
打印后
打印中
打印前
in.
panic: 触发异常

defer语句执行顺序为后进先出
当出现panic之后会先执行完defer语句。最后panic(panic之后的语句不再执行)
```
