#### 1. 下面代码有什么问题？

```go
package main

import (
	"fmt"
	"runtime"
)

func main() {
	runtime.GOMAXPROCS(1)
	go func() {
		for i := 0; i < 10; i++ {
			fmt.Println(i)
		}
	}()
	for {
	}
}
```

#### 1. 答案&解析

```text
for {} 独占CPU资源导致其它goroutine饿死(避免使用死循环)
可以通过阻塞的方式避免CPU占用(select模式)
代码修复为：
package main

import (
	"fmt"
	"os"
	"runtime"
)

func main() {
	runtime.GOMAXPROCS(1)
	go func() {
		for i := 0; i < 10; i++ {
			fmt.Println(i)
		}
		os.Exit(0)
	}()
	select {}
}
```

#### 2. 假设x已声明，y未声明，下面4行代码那些是正确的？

```go
x, _ := f()  // 1
x, _ = f()   // 2
x, y := f()  // 3
x, y = f()   // 4
```

#### 2. 答案&解析

```text
2,3正确

简短变量声明：
1. 只能用于函数内部
2. 短变量声明语句中至少要声明一个新的变量
```
