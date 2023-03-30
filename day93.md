#### 1. 关于main()函数，下面说法正确的是？

```go
// A. 不能带参数
// B. 不能定义返回值
// C. 所在的包必须为main包
// D. 可以使用flag包来获取和解析命令行参数
```

#### 1. 答案&解析

```text
ABCD
```

#### 2. 下面代码能编译通过吗？

```go
package main

import "fmt"

type User struct {
	Name string
}

func (u *User) SetName(name string) {
	u.Name = name
	fmt.Printf(u.Name)
}

type Employee User

func main() {
	employee := new(Employee)
	employee.SetName("Jack")
}
```

#### 2. 答案&解析

```text
编译失败

当使用type声明一个新类型时，它不会继承原有类型的方法集
```
