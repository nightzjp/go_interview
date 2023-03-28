#### 1. 关于无缓冲和有冲突的channel，下面说法正确的是？

```go
// A. 无缓冲的channel是默认的缓冲为1的channel
// B. 无缓冲的channel和有缓冲的channel都是同步的
// C. 无缓冲的channel和有缓冲的channel都是异步的
// D. 无缓冲的channel是同步的，有缓冲的channel是异步的
```

#### 1. 答案&解析

```text
D
```

#### 2. 下面代码是否能编译通过？如果通过输出什么？

```go
package main

import "fmt"

func Foo(x interface{}) {
	if x == nil {
		fmt.Println("empty interface")
		return
	}
	fmt.Println("non-empty interface")
}

func main() {
	var x *int = nil
	Foo(x)
}
```

#### 2. 答案&解析

```text
non-empty interface

当且仅当动态类型和值类型都为nil时，接口类型值才为nil
```

#### 3. 下面代码输出什么？

```go
package main

import (
	"fmt"
	"time"
)

func main() {
	ch := make(chan int, 100)
	// A.
	go func() {
		for i := 0; i < 10; i++ {
			ch <- i
		}
	}()
	// B.
	go func() {
		for {
			a, ok := <-ch
			if !ok {
				fmt.Println("close")
				return
			}
			fmt.Println("a: ", a)
		}
	}()
	close(ch)
	fmt.Println("ok")
	time.Sleep(time.Second * 10)
}
```

#### 3. 答案&解析

```text
程序异常

当协程A还没开始的时候。主协程已经将channel关闭了。
```
