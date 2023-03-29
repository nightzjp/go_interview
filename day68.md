#### 1. 下面代码有什么问题吗？

```go
package main

import "fmt"

func main() {
	for i := 0; i < 10; i++ {
	loop:
		fmt.Println(i)
		goto loop
	}
}
```

#### 1. 答案&解析

```text
编译报错

goto不能跳转到其它函数或内层代码
```

#### 2. 下面代码输出什么？

```go
package main

import "fmt"

func main() {
	x := []int{0, 1, 2}
	y := [3]*int{}
	for i, v := range x {
		defer func() {
			fmt.Println(v)
		}()
		y[i] = &v
	}
	fmt.Println(*y[0], *y[1], *y[2])
}
```

#### 2. 答案&解析

```text
222
2
2
2
```
