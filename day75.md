#### 1. 下面代码有什么问题，请说明？

```go
package main

import (
	"fmt"
	"io/ioutil"
	"os"
)

func main() {
	f, err := os.Open("file")
	defer f.Close()
	if err != nil {
		return
	}
	b, err := ioutil.ReadAll(f)
	fmt.Println(string(b))
}
```

#### 1. 答案&解析

```text
defer语句应该放在if语句的后边，先判断err，再defer关闭文件句柄。
代码修复为：

package main

import (
	"fmt"
	"io/ioutil"
	"os"
)

func main() {
	f, err := os.Open("file")
	if err != nil {
		return
	}
	defer f.Close()
	b, err := ioutil.ReadAll(f)
	fmt.Println(string(b))
}
```

#### 2. 下面代码输出什么？

```go
package main

import "fmt"

func f() {
	defer func() {
		if r := recover(); r != nil {
			fmt.Printf("recover:%#v", r)
		}
	}()
	panic(1)
	panic(2)
}

func main() {
	f()
}
```

#### 2. 答案&解析

```text
recover:1.

当程序panic时就不会往下执行，可以使用recover()捕获panic的内容
```
