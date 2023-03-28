#### 1. 下面代码输出什么？

```go
package main

import "fmt"

func main() {
	var ch chan int
	select {
	case v, ok := <-ch:
		fmt.Println(v, ok)
	default:
		panic("default")
	}
}
```

#### 1. 答案&解析

```text
default

ch为nil，读写都会阻塞，走默认default
```

#### 2. 下面代码输出什么？

```go
package main

import (
	"encoding/json"
	"fmt"
)

type People struct {
	name string `json:"name"`
}

func main() {
	js := `{
		"name": "seekload"
	}`
	var p People
	err := json.Unmarshal([]byte(js), &p)
	if err != nil {
		fmt.Println("err: ", err)
		return
	}
	fmt.Println(p)
}
```

#### 2. 答案&解析

```text
输出{}

结构体的字段首字母小写。不可被导出。
修复代码：
type People struct {
	Name string `json:"name"`
}
```
