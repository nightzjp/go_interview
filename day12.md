#### 1. 下面属于go语言关键字的有哪些？

```go
// A. func
// B. struct
// C. class
// D. defer
```

#### 1. 答案&解析

```text
ABD。

go语言有25个关键字
break default     func interface select
case  defer       go   map       struct
chan  else        goto package   switch
const fallthrough if   range     type
for   continue    var  import    return
```

#### 2. 下面这段代码输出什么？

```go
package main

import "fmt"

func main() {
	i := -5
	j := +5
	fmt.Printf("%+d %+d", i, j)
}

// A. -5 +5
// B. +5 +5
// C. 0 0
```

#### 2. 答案&解析

```text
A。

%的表示输出十进制数字，+表示输出数值的符号
```

#### 3. 下面这段代码输出什么？

```go
package main

import "fmt"

type People struct{}

func (p *People) ShowA() {
	fmt.Println("showA")
	p.ShowB()
}

func (p *People) ShowB() {
	fmt.Println("showB")
}

type Teacher struct {
	People
}

func (t *Teacher) ShowB() {
	fmt.Println("teacher showB")
}

func main() {
	t := Teacher{}
	t.ShowB()
}
```

#### 3. 答案&解析

```text
teacher showB。

1. 在嵌套结构体中，People称为内部类型，Teacher称为外部类型；通过嵌套，内部的属性、方法，可以作为外部类型所有，就好像是自己的一样。
2. 此外，外部还可以定义自己的属性和方法，甚至可以定义同名的方法。这样内部的方法就会被覆盖。
```
