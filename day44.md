#### 1. 下面代码有什么问题？

```go
package main

func main() {
	m := make(map[string]int, 2)
	cap(m)
}
```

#### 1. 答案&解析

```text
cap()函数仅适用于数组、数组指针、slice和channel，不适用于map。可以使用len()返回map的元素个数
```

#### 2. 下面的代码有什么问题？

```go
package main

func main() {
	var x = nil
	_ = x
}
```

#### 2. 答案&解析

```text
nil用于表示interface、函数、map、slice和channels的零值。如果不指定变量类型，编译器猜不出具体的变量类型会报错。
修复代码：

package main

func main() {
	var x interface{} = nil
	_ = x
}
```

#### 3. 下面代码能编译通过吗？

```go
package main

import "fmt"

type info struct {
	result int
}

func work() (int, error) {
	return 13, nil
}

func main() {
	var data info
	data.result, err := work()
	fmt.Println("info: %+v\n", data)
}
```

#### 3. 答案&解析

```text
不能使用短变量声明结构体字段。
修复代码：
package main

import "fmt"

type info struct {
	result int
}

func work() (int, error) {
	return 13, nil
}

func main() {
	var data info
	var err error
	data.result, err = work()
	if err != nil {
		fmt.Println(err)
		return
	}
	fmt.Println("info: %+v\n", data)
}
```
