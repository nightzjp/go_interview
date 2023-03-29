#### 1. 关于字符串连接，下面语法正确的是？

```go
// A. str := 'abc' + '123'
// B. str := "abc" + "123"
// C. str := '123' + "abc"
// D. fmt.Sprintf("abc%d", 123)
```

#### 1. 答案&解析

```text
BD 

在go语言中。双引号表示字符串string，其本质是byte类型的数组，单引号表示字符，即rune类型
```

#### 2. 下面的代码能编译通过吗？如果可以，输出什么？

```go
package main

import "fmt"

func DeferTest1(i int) (r int) {
	r = i
	defer func() {
		r += 3
	}()
	return r
}

func DeferTest2(i int) (r int) {
	defer func() {
		r += i
	}()
	return 2
}

func main() {
	fmt.Println(DeferTest1(1))
	fmt.Println(DeferTest2(1))
}
```

#### 2. 答案&解析

```text
4 3

命名返回值
```
