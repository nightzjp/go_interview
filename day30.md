#### 1. 下面这段代码输出什么？

```go
package main

import "fmt"

func f(n int) (r int) {
	defer func() {
		r += n
		recover()
	}()
	var f func()
	defer f()
	f = func() {
		r += 2
	}
	return n + 1
}

func main() {
	fmt.Println(f(3))
}
```

#### 1. 答案&解析

```text
7

命名返回值
```

#### 2. 下面这段代码输出什么？

```go
package main

import "fmt"

func main() {
	var a = [5]int{1, 2, 3, 4, 5}
	var r [5]int

	for i, v := range a {
		if i == 0 {
			a[1] = 12
			a[2] = 13
		}
		r[i] = v
	}
	fmt.Println("r = ", r)
	fmt.Println("a = ", a)
}
```

#### 2. 答案&解析

```text
r =  [1 2 3 4 5]
a =  [1 12 13 4 5]

range表达式是副本参与循环。无论a被如何修改。b依旧保持原值。如果想要r和a的输出一样。则可以修改为
package main

import "fmt"

func main() {
	var a = [5]int{1, 2, 3, 4, 5}
	var r [5]int

	for i, v := range &a {
		if i == 0 {
			a[1] = 12
			a[2] = 13
		}
		r[i] = v
	}
	fmt.Println("r = ", r)
	fmt.Println("a = ", a)
}
```
