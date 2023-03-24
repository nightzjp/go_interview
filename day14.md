#### 1. 下面代码输出什么？

```go
func main() {
	str := "hello"
	str[0] = "x"
	fmt.Println(str)
}
// A. hello
// B. xello
// C. compilation error
```

#### 1. 答案&解析

```text
C。

go语言中的字符串是只读的。可以通过string->bytes->string实现类型效果
```

#### 2. 下面代码输出什么？

```go
package main

import "fmt"

func incr(p *int) int {
	*p++
	return *p
}

func main() {
	p := 1
	incr(&p)
	fmt.Println(p)
}
// A. 1
// B. 2
// C. 3
```

#### 2. 答案&解析

```text
B。

incr()函数里的p是*int类型的指针，指向的是main()函数的变量p的地址。对指针进行递增操作，然后返回自增后的结果
```

#### 3. 对add()函数调用正确的是？

```go
func add(args ...int) int {
	sum := 0
	for _, arg := range args {
		sum += arg
	}
	return sum
}
// A. add(1, 2)
// B. add(1, 3, 7)
// C. add([]int{1, 2})
// D. add([]int{1, 3, 7}...)
```

#### 4. 答案&解析

```text
ABD。

函数可变函数的传参
```