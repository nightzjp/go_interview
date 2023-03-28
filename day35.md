#### 1. 关于bool变量b的赋值，下面错误的用法是？

```go
// A. b = true
// B. b = 1
// C. b = bool(1)
// D. b = (1 == 2)
```

#### 1. 答案&解析

```text
BC
```

#### 2. 关于变量的自增和自减操作，下面语句正确的是？

```go
// A. 
i := 1
i++

// B.
i := 1
j = i++

// C.
i := 1
++i

// D.
i := 1
i--
```

#### 2. 答案&解析

```text
AD

go语言中只有i++跟i--
```

#### 3. 关于GetPodAction定义，下面赋值正确的是？

```go
package main

type Fragment interface {
	Exec(transInfo *TransInfo) error
}

type GetPodAction struct {}

func (g GetPodAction) Exec(transInfo *TransInfo) error {
	return nil
}

func main() {

}

// A. var fragment Fragment = new(GetPodAction)
// B. var fragment Fragment = GetPodAction{}
// C. var fragment Fragment = &GetPodAction{}
// D. var fragment Fragment = GetPodAction{}
```

#### 3. 答案&解析

```text
ACD
```
