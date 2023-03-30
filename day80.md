#### 1. 定义一个包内全局字符串变量，下面语法正确的是？

```go
// A. var str string
// B. str := ""
// C. str = ""
// D. var str = ""
```

#### 1. 答案&解析

```text
AD

全局变量需要定义在函数之外，使用var关键字
```

#### 2. 下面代码有什么问题？

```go
package main

import (
	"fmt"
	"sync"
)

func main() {
	wg := sync.WaitGroup{}
	for i := 0; i < 5; i++ {
		go func(wg sync.WaitGroup, i int) {
			wg.Add(1)
			fmt.Printf("i:%d\n", i)
			wg.Done()
		}(wg, i)
	}
	wg.Wait()
	fmt.Println("exit")
}
```

#### 2. 答案&解析

```text
WaitGroup的使用存在两个问题
1. 在协程中使用了wg.Add()
2. 使用了*sync.WaitGroup副本

修复方式1：
package main

import (
	"fmt"
	"sync"
)

func main() {
	wg := sync.WaitGroup{}
	for i := 0; i < 5; i++ {
		wg.Add(1)
		go func(i int) {
			fmt.Printf("i:%d\n", i)
			wg.Done()
		}(i)
	}
	wg.Wait()
	fmt.Println("exit")
}

修复方式2：
package main

import (
	"fmt"
	"sync"
)

func main() {
	wg := &sync.WaitGroup{}
	for i := 0; i < 5; i++ {
		wg.Add(1)
		go func(wg *sync.WaitGroup, i int) {
			fmt.Printf("i:%d\n", i)
			wg.Done()
		}(wg, i)
	}
	wg.Wait()
	fmt.Println("exit")
}
```
