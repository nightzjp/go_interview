#### 1. 下面的代码输出什么？

```go
package main

import "fmt"

type T struct {
	n int
}

func main() {
	ts := [2]T{}
	for i, t := range ts {
		switch i {
		case 0:
			t.n = 3
			ts[1].n = 9
		case 1:
			fmt.Println(t.n)
		}
	}
	fmt.Println(ts)
}
```

#### 1. 答案&解析

```text
0 [{0} {9}]

for-range循环数组。此时使用的是ts的副本，所以t.n = 3的赋值不会影响原数组
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
	for i, t := range &ts {
		switch i {
		case 0:
			t.n = 3
			ts[1].n = 9
		case 1:
			fmt.Println(t.n)
		}
	}
	fmt.Println(ts)
}
```

#### 2. 答案&解析

```text
9 [{0} {9}]
```
