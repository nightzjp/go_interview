#### 1. 通过指针变量p访问其成员变量name有那几种方式？

```go
// A. p.name
// B. (&p).name
// C. (*p).name
// D. p->name
```

#### 1. 答案&解析

```text
AC。 &为取址运算符，*为指针的引用
```

#### 2. 下面这段代码有什么问题？

```go
package main

import "fmt"

type MyInt1 int
type MyInt2 = int

func main() {
	var i int = 0
	var i1 MyInt1 = i
	var i2 MyInt2 = i
	fmt.Println(i1, i2)
}

```

#### 2. 答案&解析

```text
编译失败

第五行代码基于int类型创建了新类型MyInt1.第六行则是创建了别名。
可以强制类型转换: var i1 MyInt1 = MyInt1(i)
```

