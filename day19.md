#### 1. 下面代码段输出什么？

```go
package main

import "fmt"

type Person struct {
	age int
}

func main() {
	person := &Person{28}

	// 1.
	defer fmt.Println(person.age)

	// 2.
	defer func(p *Person) {
		fmt.Println(p.age)
	}(person)

	// 3.
	defer func() {
		fmt.Println(person.age)
	}()

	person.age = 29
}
```

#### 1. 答案&解析

```text
29 29 28

1. person.age 此时是将28作为defer函数的参数
2. defer缓存的是结构体Person{28}的地址。最终age被重新赋值为29
3. 闭包引用
```
