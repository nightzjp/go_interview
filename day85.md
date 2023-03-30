#### 1. 下面这段代码输出什么？

```go
package main

import (
	"fmt"
	"strings"
)

func main() {
	fmt.Println(strings.TrimRight("ABBA", "BA"))
}
```

#### 1. 答案&解析

```text
输出空字符串。

TrimRight()会将第二个参数字符串里面的所有字符拿出来处理，只要与其中任何一个字符向东，便会将其删除。
```

#### 2. 下面代码输出什么？

```go
package main

import "fmt"

func main() {
	var src, dst []int
	src = []int{1, 2, 3}
	copy(dst, src)
	fmt.Println(dst)
}
```

#### 2. 答案&解析

```text
[]

copy(dst, src)函数返回len(dst), len(src)之间的最小值，如果要将src完全的拷贝到dst，必须给dst分配足够的内存空间。
代码修复为：
package main

import "fmt"

func main() {
	var src, dst []int
	src = []int{1, 2, 3}
	dst = make([]int, len(src))
	copy(dst, src)
	fmt.Println(dst)
}
或者使用append函数：
package main

import "fmt"

func main() {
	var src, dst []int
	src = []int{1, 2, 3}
	dst = append(dst, src...)
	fmt.Println(dst)
}
```
