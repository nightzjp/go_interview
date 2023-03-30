#### 1. 下面的代码输出什么？

```go
package main

import "fmt"

type Point struct{ x, y int }

func main() {
	s := []Point{
		{1, 2},
		{3, 4},
	}
	for _, p := range s {
		p.x, p.y = p.y, p.x
	}
	fmt.Println(s)
}
```

#### 1. 答案&解析

```text
输出 [{1 2} {3 4}].

for-range循环，获取到的是元素的副本。
代码修复为：
package main

import "fmt"

type Point struct{ x, y int }

func main() {
	s := []*Point{
		&Point{1, 2},
		&Point{3, 4},
	}
	for _, p := range s {
		p.x, p.y = p.y, p.x
	}
	fmt.Println(*s[0])
	fmt.Println(*s[1])
}
```

#### 2. 下面代码有什么隐患？

```go
package main

import "fmt"

func get() []byte {
	raw := make([]byte, 10000)
	fmt.Println(len(raw), cap(raw), &raw[0])
	return raw[:3]
}

func main() {
	data := get()
	fmt.Println(len(data), cap(data), &data[0])
}
```

#### 2. 答案&解析

```text
get()函数返回的切片与原切片公用底层数组，如果在调用函数里修改返回的切片，将会影响原切片。

可以修复为：
package main

import "fmt"

func get() []byte {
	raw := make([]byte, 10000)
	fmt.Println(len(raw), cap(raw), &raw[0])
	res := make([]byte, 3)
	copy(res, raw[:3])
	return res
}

func main() {
	data := get()
	fmt.Println(len(data), cap(data), &data[0])
}
```
