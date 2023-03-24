#### 1. 下面这段代码有什么问题？

```go
package main

import "fmt"

func main() {
	sn1 := struct {
		age  int
		name string
	}{age: 26, name: "张建平"}
	sn2 := struct {
		age  int
		name string
	}{age: 26, name: "张建平"}

	if sn1 == sn2 {
		fmt.Println("sn1 == sn2")
	}

	sm1 := struct {
		age int
		m   map[string]string
	}{age: 27, m: map[string]string{"name": "张建平"}}
	sm2 := struct {
		age int
		m   map[string]string
	}{age: 27, m: map[string]string{"name": "张建平"}}

	if sm1 == sm2 {
		fmt.Println("sm1 == sm2")
	}
}

```

#### 1. 答案&解析

```text
编译无法通过

1. 结构体只能比较是否相等，不能比较大小
2. 相同类型的结构体才能比较，结构体相同但是属性不相同不可比较
3. 布尔，数值，字符串，指针，数组可以比较。
4. 切片，map以及函数不可以比较
```
