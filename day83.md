#### 1. 同级文件的包名不允许有多个，是否正确？

```go
// A. true
// B. false
```

#### 1. 答案&解析

```text
A. 

一个文件夹下只能有一个包，但是可以有多个.go文件，这些文件都属于同一个包
```

#### 2. 下面的代码有什么问题？

```go
package main

import "fmt"

type data struct {
	name string
}

func (d *data) print() {
	fmt.Println("name: ", d.name)
}

type printer interface {
	print()
}

func main() {
	d1 := data{"one"}
	d1.print()

	var in printer = data{"two"}
	in.print()
}
```

#### 2. 答案&解析

```text
结构体类型data没有实现接口printer。

可修复为：
package main

import "fmt"

type data struct {
	name string
}

func (d data) print() {
	fmt.Println("name: ", d.name)
}

type printer interface {
	print()
}

func main() {
	d1 := data{"one"}
	d1.print()

	var in printer = data{"two"}
	in.print()
}
```
