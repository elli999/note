
<!-- vim-markdown-toc Redcarpet -->

+ [一、函数的概念](#一、函数的概念)
    * [1.1 什么是函数](#1-1-什么是函数)
    * [1.2 函数的声明](#1-2-函数的声明)
    * [1.3 函数的使用](#1-3-函数的使用)
+ [二、函数的参数](#二、函数的参数)
    * [2.1 参数的使用](#2-1-参数的使用)
    * [2.2 可变参](#2-2-可变参)
    * [2.3 参数传递](#2-3-参数传递)
+ [三、函数的返回值](#三、函数的返回值)
    * [3.1 什么是函数的返回值](#3-1-什么是函数的返回值)
    * [3.2 一个函数可以返回多个值](#3-2-一个函数可以返回多个值)
    * [3.3 空白标识符](#3-3-空白标识符)
+ [四、函数的作用域](#四、函数的作用域)
    * [4.1 局部变量](#4-1-局部变量)
    * [4.2 全局变量](#4-2-全局变量)
+ [五、函数的本质](#五、函数的本质)
    * [六、defer](#六、defer)
        - [defer概念](#defer概念)
        - [defer的使用情境](#defer的使用情境)
        - [多个defer](#多个defer)
        - [defer函数的参数传递](#defer函数的参数传递)
        - [EK未消化的原始内容](#ek未消化的原始内容)
+ [EK个人笔记](#ek个人笔记)
    * [定义](#定义)
    * [调用](#调用)
    * [形参](#形参)
    * [实参](#实参)
    * [可变参](#可变参)
    * [局部变量](#局部变量)
    * [全局变量](#全局变量)
    * [recursion递归函数](#recursion递归函数)
    * [defer](#defer)
    * [匿名函数](#匿名函数)

<!-- vim-markdown-toc -->

# 一、函数的概念

## 1.1 什么是函数

函数是执行特定任务的代码块。

## 1.2 函数的声明

go语言至少有一个main函数

语法格式：

```go
func funcName(parametername type1, parametername type2) (output1 type1, output2 type2) {
//这里是处理逻辑代码
//返回多个值
return value1, value2
}
```

- func：函数由 func 开始声明
- funcName：函数名称，函数名和参数列表一起构成了函数签名。
- parametername type：参数列表，参数就像一个占位符，当函数被调用时，你可以将值传递给参数，这个值被称为实际参数。参数列表指定的是参数类型、顺序、及参数个数。参数是可选的，也就是说函数也可以不包含参数。
- output1 type1, output2 type2：返回类型，函数返回一列值。return_types 是该列值的数据类型。有些功能不需要返回值，这种情况下 return_types 不是必须的。
- 上面返回值声明了两个变量output1和output2，如果你不想声明也可以，直接就两个类型。
- 如果只有一个返回值且不声明返回值变量，那么你可以省略包括返回值的括号（即一个返回值可以不声明返回类型）
- 函数体：函数定义的代码集合。

## 1.3 函数的使用

示例代码：

```go
package main

import "fmt"

func main() {
   /* 定义局部变量 */
   var a int = 100
   var b int = 200
   var ret int

   /* 调用函数并返回最大值 */
   ret = max(a, b)

   fmt.Printf( "最大值是 : %d\n", ret )
}

/* 函数返回两个数的最大值 */
func max(num1, num2 int) int {
   /* 定义局部变量 */
   var result int

   if (num1 > num2) {
      result = num1
   } else {
      result = num2
   }
   return result 
}
```

运行结果：

```go
最大值是 : 200
```





# 二、函数的参数

## 2.1 参数的使用

形式参数：定义函数时，用于接收外部传入的数据，叫做形式参数，简称形参。

实际参数：调用函数时，传给形参的实际的数据，叫做实际参数，简称实参。

函数调用：

	A：函数名称必须匹配
	
	B：实参与形参必须一一对应：顺序，个数，类型

## 2.2 可变参

Go函数支持变参。接受变参的函数是有着不定数量的参数的。为了做到这点，首先需要定义函数使其接受变参：

```go
func myfunc(arg ...int) {}
```

`arg ...int`告诉Go这个函数接受不定数量的参数。注意，这些参数的类型全部是int。在函数体中，变量arg是一个int的slice：

```go
for _, n := range arg {
fmt.Printf("And the number is: %d\n", n)
}
```

## 2.3 参数传递

go语言函数的参数也是存在**值传递**和**引用传递**

函数运用场景

**值传递**

```go
package main

import (
   "fmt"
   "math"
)

func main(){
   /* 声明函数变量 */
   getSquareRoot := func(x float64) float64 {
      return math.Sqrt(x)
   }

   /* 使用函数 */
   fmt.Println(getSquareRoot(9))

}
```

**引用传递**

这就牵扯到了所谓的指针。我们知道，变量在内存中是存放于一定地址上的，修改变量实际是修改变量地址处的内
存。只有add1函数知道x变量所在的地址，才能修改x变量的值。所以我们需要将x所在地址&x传入函数，并将函数的参数的类型由int改为*int，即改为指针类型，才能在函数中修改x变量的值。此时参数仍然是按copy传递的，只是copy的是一个指针。请看下面的例子

```go
package main
import "fmt"
//简单的一个函数，实现了参数+1的操作
func add1(a *int) int { // 请注意，
*a = *a+1 // 修改了a的值
return *a // 返回新值
} f
unc main() {
x := 3
fmt.Println("x = ", x) // 应该输出 "x = 3"
x1 := add1(&x) // 调用 add1(&x) 传x的地址
fmt.Println("x+1 = ", x1) // 应该输出 "x+1 = 4"
fmt.Println("x = ", x) // 应该输出 "x = 4"
}
```

- 传指针使得多个函数能操作同一个对象。
- 传指针比较轻量级 (8bytes),只是传内存地址，我们可以用指针传递体积大的结构体。如果用参数值传递的话, 在每次copy上面就会花费相对较多的系统开销（内存和时间）。所以当你要传递大的结构体的时候，用指针是一个明智的选择。
- **Go语言中slice，map这三种类型的实现机制类似指针**，所以可以直接传递，而不用取地址后传递指针。（注：若函数需改变slice的长度，则仍需要取地址传递指针）



# 三、函数的返回值

## 3.1 什么是函数的返回值

一个函数被调用后，返回给调用处的执行结果，叫做函数的返回值。

调用处需要使用变量接收该结果

## 3.2 一个函数可以返回多个值

一个函数可以没有返回值，也可以有一个返回值，也可以有返回多个值。

```go
package main

import "fmt"

func swap(x, y string) (string, string) {
   return y, x
}

func main() {
   a, b := swap("Mahesh", "Kumar")
   fmt.Println(a, b)
}
```

```go
func SumAndProduct(A, B int) (add int, Multiplied int) {
add = A+B
Multiplied = A*B
return
}
```
## 3.3 空白标识符

_是Go中的空白标识符。它可以代替任何类型的任何值。让我们看看这个空白标识符的用法。

比如rectProps函数返回的结果是面积和周长，如果我们只要面积，不要周长，就可以使用空白标识符。

示例代码：

```go
package main

import (  
    "fmt"
)

func rectProps(length, width float64) (float64, float64) {  
    var area = length * width
    var perimeter = (length + width) * 2
    return area, perimeter
}
func main() {  
    area, _ := rectProps(10.8, 5.6) // perimeter is discarded
    fmt.Printf("Area %f ", area)
}
```



# 四、函数的作用域

作用域：变量可以使用的范围。

## 4.1 局部变量

一个函数内部定义的变量，就叫做局部变量

变量在哪里定义，就只能在哪个范围使用，超出这个范围，我们认为变量就被销毁了。

## 4.2 全局变量

一个函数外部定义的变量，就叫做全局变量

所有的函数都可以使用，而且共享这一份数据



# 五、函数的本质

函数也是Go语言中的一种数据类型，可以作为另一个函数的参数，也可以作为另一个函数的返回值。

---

## 六、defer

https://www.bilibili.com/video/BV1jJ411c7s3?p=73

### defer概念

`defer`是“延迟”、“推迟”的意思。


（EK不确定）在Go语言中，一般使用defer关键字来延迟function或方法的执行。函数内部使用`defer`时，该函数的执行顺序是：1.正常语句 2.defer语句（逆序） 3.return语句。

> EK: `defer`貌似可以在任意语句中使用。

### defer的使用情境

例如程序需要打开文件`文件.open()`进行编辑，我们往往容易忘记在最后加上一行关闭指令，这个时候就可以这样做：

```Go
文件.open()
defer close()
编辑的代码
```

### 多个defer

当一个函数有多个defer时，它们被添加到一个堆栈中，并在Last In, First Out（LIFO）后进先出的顺序中执行。

> Last In, First Out: 最后一个进入的会被第一个调用出来。可以想象成一个桶，defer丢进去之后，是从下往上堆起来的，但是取出的时候只能从上往下逐个取。

### defer函数的参数传递

defer函数是延迟执行函数内部代码，但是值传递会正常发生。

```Go
func main() {
    a := 2
    fmt.Println(a)  //  2
    defer fun1(a)  //  程序执行到这一行时已经把值“2”传递进去了
    a++
    fmt.Print("main中的a值：", a)  //  3
}

func fun1(a int) {  //  2
    fmt.Println("fun1函数中打印出来的a值：", a)
}
```

### EK未消化的原始内容

```
defer函数：
当外围函数中的代码引发运行恐慌时，只有其中所有的延迟函数都执行完毕后，该运行时恐慌才会真正被扩展至调用函数。
```

--------------------------------------------------------------------------------------------------------


# EK个人笔记

## 定义

```Go
func funcName(parametername type1, parametername type2) (output1 type1, output2 type2) {
    // 这里是处理逻辑代码
    // 返回多个值
    return value1, value2
}
```

## 调用

```Go
funcName()
```


## 形参

形式参数：也叫形参。函数定义时<++>

## 实参

xxxx 实际传入的xxx

## 可变参

**概念：** 一个函数的参数类型确定，但是个数不确定，就可以使用可变参数。

**格式：**

```Go
func myfunc(arg ... type) {
    ...
}
```

**注意事项：**

* <++>

## 局部变量

函数内部定义的变量，就叫做局部变量。

## 全局变量

函数外部定义的变量，就叫做全局变量。

* 全局变量不支持简短定义方法。 `num1 := 100` 是不行的，要这样`var num1 = 100`。

## recursion递归函数

一个函数自己调用自己，就叫做递归函数。

递归函数要有一个出口，逐渐的向出口靠近。

## defer

defer是延迟、推迟函数的执行。

## 匿名函数

没有名字的函数。

**Exapmle:**

```Go
func (){
    // 内容
}()
```

* 最后一个括号表示直接调用，如果要传参，也是在这个括号内。
* 一般情况下只能调用一次，除非把这个function赋值给某个函数变量。

```Go
res1 := func (a, b int)int{
    return a + b
}(10, 20)

res2 := func (a, b int)int{
    return a + b
}
fmt.Println(res2(10, 20)) ???
```

res1 是把结果赋值给res1，res1是int型 ？？
res2 是把函数赋值给res2，res2是函数变量 

--------------------------------------------------------------------------------------------------------


