---
layout: pose
title: Go 学习之路：引用类型与值类型
date: 2017-10-03 23:19:20
tags: [go,引用类型,值类型]
categories: [后端,go]
cover: https://ss0.bdstatic.com/70cFvHSh_Q1YnxGkpoWK1HF6hhy/it/u=3407284977,848411949&fm=26&gp=0.jpg
---
#### Golang中只有三种引用类型：slice(切片)、map(字典)、channel(管道)；

### 引用类型
- **引用类型理解为（C语言）：指针**

### 值类型
* 值的拷贝

下面以值类型和slice(切片)例子可知：
```
package main

import "fmt"

func main(){
	a := [5]int{2, 3, 4, 5, 6}
	b := a
	fmt.Println(a,b)
	b[2] = 77
	fmt.Println(a,b)
}
```
上面定义了一个数组a，它是值类型，复制给b是copy，当b发生变化后a并不会发生任何变化，结果如下： 
![值类型](https://img-blog.csdn.net/20180628152152653?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzE1NDEzMDA5/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

```
package main

import "fmt"

func main(){
	a := []int{2, 3, 4, 5, 6}
	b := a
	fmt.Println(a,b)
	b[2] = 77
	fmt.Println(a,b)
}
```
上面定义了一个数组a，它是引用类型（slice切片），被b引用（指针）后，当b发生变化后a也发生任何变化，结果如下： 
![引用类型](https://img-blog.csdn.net/20180628152701354?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzE1NDEzMDA5/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)



