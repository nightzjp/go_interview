#### 1. 关于字符串连接，下面语法正确的是？

```go
// A. str := 'abc' + '123'
// B. str := "abc" + "123"
// C. str := 'abc' + "123"
// D. fmt.Sprintf("abc%d", 123)
```

#### 1. 答案&解析

```text
BD。 字符串连接使用双引号或fmt格式化。除此之外还有strings.Join(), buffer.WriteString()等
```

#### 2. 下面的代码能否编译通过？如果可以输出什么？

```go
package main

import "fmt"

const (
	x = iota
	_
	y
	z = "zz"
	k
	p = iota
)

func main() {
	fmt.Println(x, y, z, k, p)
}
```

#### 2. 答案&解析

```text
0 2 zz zz 5

iota的使用
iota在const里面初始为0，逐行+1，当再次在const声明时为0
```

#### 3. 下面赋值正确的是？

```go
// A. var x = nil
// B. var x interface{} = nil
// C. var x string = nil
// D. var x error = nil
```

#### 3. 答案&解析

```text
BD。 

nil值只能赋值给指针、chan、func、interface、map或slice类型的变量
```
