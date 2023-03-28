#### 1. 下面这段代码输出结果正确吗？

```go
import "fmt"

type Foo struct {
	bar string
}

func main() {
	s1 := []Foo{
		{"A"},
		{"B"},
		{"C"},
	}
	s2 := make([]*Foo, len(s1))
	for i, value := range s1 {
		s2[i] = &value
	}
	fmt.Println(s1[0], s1[1], s1[2])
	fmt.Println(s2[0], s2[1], s2[2])
}

// 输出：
// {A} {B} {C}
// &{A} &{B} &{C}
```

#### 1. 答案&解析

```text
s2输出结果错误。输出结果为：&{C} &{C} &{C}

有两种解决方式：
for i, value := range s1 {
	value := value
	s2[i] = &value
}

for i := range s1 {
	s2[i] = &s1[i]
}
```

#### 2. 下面代码里的counter输出值为？

```go
package main

import "fmt"

func main() {
	var m = map[string]int{
		"A": 21,
		"B": 22,
		"C": 23,
	}
	counter := 0
	for k, v := range m {
		if counter == 0 {
			delete(m, "A")
		}
		counter++
		fmt.Println(k, v)
	}
	fmt.Println("counter is ", counter)
}
// A. 2
// B. 3
// C. 2 或 3
```

#### 2. 答案&解析

```text
C.

for range map是无序的，如果第一次循环到A输出3， 否则输出2
```
