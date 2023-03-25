#### 1. 下面这段代码正确的输出是什么？

```go
package main

import "fmt"

func f() {
	defer fmt.Println("D")
	fmt.Println("F")
}

func main() {
	f()
	fmt.Println("M")
}

// A. F M D
// B. D F M
// C. F D M
```

#### 1. 答案&解析

```text
C。

defer
```

#### 2. 下面代码输出什么？

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
	
	person = &Person{29}
}
```

#### 2. 答案&解析

```text
29 28 28

1. 将28作为defer函数的参数。会将28缓存
2. defer缓存的是结构体Person{28}的值
3. 闭包引用
```
