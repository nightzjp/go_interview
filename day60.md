#### 1. 下面哪一行代码因引发panic，请说明原因.

```go
package main

type T struct{}

func (t *T) foo() {}

func (t T) bar() {}

type S struct {
	*T
}

func main() {
	s := S{}
	_ = s.foo
	s.foo()
	_ = s.bar
}
```

#### 1. 答案&解析

```text
第17行

x.bar将被展开为(*s.T).bar,而s.T是个空指针，会引发panic
```

#### 2. 下面的代码有什么问题？

```go
package main

import (
	"fmt"
	"sync"
	"time"
)

type data struct {
	sync.Mutex
}

func (d data) test(s string) {
	d.Lock()
	defer d.Unlock()

	for i := 0; i < 5; i++ {
		fmt.Println(s, i)
		time.Sleep(time.Second)
	}
}

func main() {
	var wg sync.WaitGroup

	wg.Add(2)
	var d data

	go func() {
		defer wg.Done()
		d.test("read")
	}()

	go func() {
		defer wg.Done()
		d.test("write")
	}()

	wg.Wait()
}
```

#### 2. 答案&解析

```text
锁会失效。

将Mutex作为匿名字段时，相关方法必须使用指针接受者，否则会导致锁失效。
代码修复为：
func (d *data) test(s string) {
	d.Lock()
	defer d.Unlock()

	for i := 0; i < 5; i++ {
		fmt.Println(s, i)
		time.Sleep(time.Second)
	}
}
或：
package main

import (
	"fmt"
	"sync"
	"time"
)

type data struct {
	*sync.Mutex  // 指针嵌入
}

func (d data) test(s string) {
	d.Lock()
	defer d.Unlock()

	for i := 0; i < 5; i++ {
		fmt.Println(s, i)
		time.Sleep(time.Second)
	}
}

func main() {
	var wg sync.WaitGroup

	wg.Add(2)
	d := data{new(sync.Mutex)}  // 需要初始化

	go func() {
		defer wg.Done()
		d.test("read")
	}()

	go func() {
		defer wg.Done()
		d.test("write")
	}()

	wg.Wait()
}
```
