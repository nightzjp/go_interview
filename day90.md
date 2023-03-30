#### 1. 下面代码能通过编译吗？

```go
package main

type T int

func F(t T) {}

func main() {
	var q int
	F(q)
}
```

#### 1. 答案&解析

```text
编译失败
F函数接收T类型，T是基于类型int创建的新类型
可修复为：
package main

type T = int

func F(t T) {}

func main() {
	var q int
	F(q)
}
```

#### 2. 下面代码能通过编译吗？请简要说明

```go
package main

type T []int

func F(t T) {}

func main() {
	var q []int
	F(q)
}
```

#### 2. 答案&解析

```text
编译通过

对于地城类型相同的变量可以相互赋值，还有一个重要条件，即至少有一个不是有名类型
Named Type有两类：
1. 内置类型比如int,int64,float,string,bool等
2. 使用关键字type声明的类型

Unnamed Type 是基于已有的Named Type组合一起的类型，例如：struct{}, []string, interface{}, map[string]bool等
```
