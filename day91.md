#### 1. 下面两段代码能否编译通过？请简要说明

```go
package main

// 1
func f() {}
func f() {}

func main() {

}

// 2
func init() {}
func init() {}

func main() {

}
```

#### 1. 答案&解析

```text
第二段可以编译通过：除init函数之外，一个包内不循序有其他同名函数。
```

#### 2. 下面代码有什么问题？

```go
package main

func (m map[string]string) Set(key string, value string) {
	m[key] = value
}

func main() {
	m := make(map[string]string)
	m.Set("A", "One")
}
```

#### 2. 答案&解析

```text
Unnamed Type不能作为方法的接受者。

修复为：
package main

type User map[string]string

func (m User) Set(key string, value string) {
	m[key] = value
}

func main() {
	m := make(User)
	m.Set("A", "One")
}
```
