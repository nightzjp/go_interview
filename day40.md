#### 1. 关于select机制，下面说法正确的是？

```go
// A. select机制用来处理异步IO问题
// B. select机制最大的一条限制是每个case语句必须是一个IO操作
// C. golang在语言级别支持select关键字
// D. select关键字的用法与switch语句非常类似，后面要带判断条件
```

#### 1. 答案&解析

```text
ABC
```

#### 2. 下面的代码有什么问题？

```go
func Stop(stop <-chan bool) {
    close(stop)
}
```

#### 2. 答案&解析

```text
有方向的channel不可被关闭
```

#### 3. 下面这段代码存在什么问题？

```go
package main

type Param map[string]interface{}

type Show struct {
	*Param
}

func main() {
	s := new(Show)
	s.Param["day"] = 2
}
```

#### 3. 答案&解析

```text
map需要初始化才能使用，指针不支持索引

可修复为：
func main() {
	s := new(Show)
	p := make(Param)
	p["day"] = 2
	s.Param = &p
	tmp := *s.Param
	fmt.Println(tmp["day"])
}
```