---
title: "一个例子学懂go语言之Array的介绍与使用"
date: 2019-08-26T18:00:57+08:00
---

在go中，数组（`array` )是指一组确定长度的元素

## 例子

```go
package main

import "fmt"

func main() {

    var a [5]int
    fmt.Println("emp:", a)

    a[4] = 100
    fmt.Println("set:", a)
    fmt.Println("get:", a[4])

    fmt.Println("len:", len(a))

    b := [5]int{1, 2, 3, 4, 5}
    fmt.Println("dcl:", b)

    var twoD [2][3]int
    for i := 0; i < 2; i++ {
        for j := 0; j < 3; j++ {
            twoD[i][j] = i + j
        }
    }
    fmt.Println("2d: ", twoD)
}
```

## 代码解析

```go
var a [5]int
fmt.Println("emp:", a)
```

这里我们创建的数组里将会包含5个`int`元素，这里我们只是定义数组而没有进行初始化，则所有的元素都会被赋予零值（`zero-valued`)就是说5个0

```go
a[4] = 100
fmt.Println("set:", a)
fmt.Println("get:", a[4])
```

我们可以使用定位下标的形式进行赋值，数组中每个元素都有自己的下标，从0开始依次递增，可以用下标获取也可以用下标赋值

```go
fmt.Println("len:", len(a))
```

go里的内建方法`len()`方法可以获取数组长度

```go
b := [5]int{1, 2, 3, 4, 5}
fmt.Println("dcl:", b)
```

这是在定义的同时对数组进行初始化

```go
var twoD [2][3]int
for i := 0; i < 2; i++ {
	for j := 0; j < 3; j++ {
		twoD[i][j] = i + j
	}
}
fmt.Println("2d: ", twoD)
```

通常数组是一维的，但你可以通过组合把数组变成多维

## 运行结果

```go
$ go run arrays.go
emp: [0 0 0 0 0]
set: [0 0 0 0 100]
get: 100
len: 5
dcl: [1 2 3 4 5]
2d:  [[0 1 2] [1 2 3]]
```

注意：数组`fmt.Println()`打印出来都是为`[v1 v2 v3 ...]`的形式