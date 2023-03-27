#### 1. 下面这段代码输出什么？

```go
package main

import "fmt"

func change(s ...int) {
	s = append(s, 3)
}

func main() {
	slice := make([]int, 5, 5)
	slice[0] = 1
	slice[1] = 2
	change(slice...)
	fmt.Println(slice)
	change(slice[0:2]...)
	fmt.Println(slice)
}
```

#### 1. 答案&解析

```text
[1 2 0 0 0]
[1 2 3 0 0]

第一次调用change()时，append()操作使切片底层数组发生了扩容，原slice的底层数组不会改变。
第二次调用的时候，使用了操作符[i:j]获取了一个新切片。这个新切片跟底层数组是重合的。修改会影响到原切片
```

#### 2. 下面这段代码输出什么？

```go
package main

import "fmt"

func main() {
	var a = []int{1, 2, 3, 4, 5}
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
r =  [1 12 13 4 5]
a =  [1 12 13 4 5]

切片在go内部结构有一个指针指向底层数组，当range表达式发生复制时，副本的指针依旧指向底层原数组，所以对切片的修改都会反应到底层数组上。
```
