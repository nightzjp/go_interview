#### 1. 下面的代码输出什么？

```go
package main

import "fmt"

type T struct {
	n int
}

func main() {
	ts := [2]T{}
	for i := range ts[:] {
		switch i {
		case 0:
			ts[1].n = 9
		case 1:
			fmt.Println(ts[i].n)
		}
	}
	fmt.Println(ts)
}
```

#### 1. 答案&解析

```text
9 [{0} {9}]

for-range切片时使用的是切片的副本，次副本切片与原数组共享底层数组
```

#### 2. 下面的代码输出什么？

```go
package main

import "fmt"

type T struct {
	n int
}

func main() {
	ts := [2]T{}
	for i := range ts[:] {
		switch t := &ts[i]; i {
		case 0:
			t.n = 3
			ts[1].n = 9
		case 1:
			fmt.Println(ts[i].n)
		}
	}
	fmt.Println(ts)
}
```

#### 2. 答案&解析

```text
9 [{3} {9}]
```
