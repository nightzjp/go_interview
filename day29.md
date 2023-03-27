#### 1. 下面这段代码能否正常结束？

```go
package main

import "fmt"

func main() {
	v := []int{1, 2, 3}
	for i := range v {
		v = append(v, i)
	}
	fmt.Println(v)
}
```

#### 1. 答案&解析

```text
代码可以正常结束。不会出现死循环。循环次数在初始化的时候就已经确定
```

#### 2. 下面这段代码输出什么？

```go
package main

import (
	"fmt"
	"time"
)

func main() {
	var m = [...]int{1, 2, 3}
	for i, v := range m {
		go func() {
			fmt.Println(i, v)
		}()
	}
	time.Sleep(time.Second * 3)
}
```

```text
2 3
2 3
2 3

for range 使用段变量生命(:=)的形式迭代变量，需要注意的是。变量i,v在每次循环体中都会被重用。而不是重新声明。
有两种解决方案

1. 使用函数传递
package main

import (
	"fmt"
	"time"
)

func main() {
	var m = [...]int{1, 2, 3}
	for i, v := range m {
		go func(i, v int) {
			fmt.Println(i, v)
		}(i, v)
	}
	time.Sleep(time.Second * 3)
}

2. 使用临时变量
package main

import (
	"fmt"
	"time"
)

func main() {
	var m = [...]int{1, 2, 3}
	for i, v := range m {
		i := i
		v := v
		go func() {
			fmt.Println(i, v)
		}()
	}
	time.Sleep(time.Second * 3)
}
```
