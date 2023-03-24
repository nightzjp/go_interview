#### 1. 关于init函数，下面说法那些是正确的？

```go
// A. 一个包中，可以包含多个init函数
// B. 程序编译时，先执行依赖包的init函数，再执行main包的init函数
// C. main包中，不能有init函数
// D. init函数可以被其它函数调用
```

#### 1. 答案&解析

```text
AB。

1. init()函数是用于程序执行前做包的初始化的函数。比如初始化包里的变量。数据库链接等
2. 一个包i可以包含多个init函数
3. init()函数不能被其它代码显示调用
...
```

#### 2. 下面这段代码输出什么以及原因？

```go
package main

import "fmt"

func hello() []string {
	return nil
}

func main() {
	h := hello
	if h == nil {
		fmt.Println("nil")
	} else {
		fmt.Println("not nil")
	}
}
// A. nil
// B. not nil
// C. compilation error
```

#### 2. 答案&解析

```text
B。

将hello这个函数名称赋值给了h，而非hello的返回值
```

#### 3. 下面这段代码能否编译通过？如果可以输出什么

```go
package main

import "fmt"

func GetValue() int {
	return 1
}

func main() {
	i := GetValue()
	switch i.(type) {
	case int:
		fmt.Println("int")
	case string:
		fmt.Println("string")
	case interface{}:
		fmt.Println("interface")
	default:
		fmt.Println("unknow")
	}
}
```

#### 3. 答案&解析

```text
编译失败。

只有接口类型才可以使用类型选择。
```
