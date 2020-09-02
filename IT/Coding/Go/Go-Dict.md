
<!-- vim-markdown-toc Redcarpet -->

* [Concept](#concept)
    - [GOROOT](#goroot)
    - [GOPATH](#gopath)
* [Usage](#usage)
    - [Naming Rule命名规则](#naming-rule命名规则)
        + [变量命名](#变量命名)
        + [常量命名](#常量命名)
    - [Main](#main)
    - [Comment注释](#comment注释)
        + [**single line comment**](#single-line-comment)
        + [**multi line comment**](#multi-line-comment)
    - [Import](#import)
    - [Compile编译](#compile编译)
    - [variable变量](#variable变量)
        + [变量的定义](#变量的定义)
        + [变量的调用](#变量的调用)
        + [全局变量](#全局变量)
    - [constant常量](#constant常量)
        + [常量的定义](#常量的定义)

<!-- vim-markdown-toc -->

---

## Concept

### GOROOT

GOROOT is GOLANG installation directory. Also is a Environment Variable and needs be written into system setting.

### GOPATH

Gopath is Go workspace that save all GO project and code file.

> Go code file `MUST` work in `GOPATH`.

> In Ubuntu, the default GOPATH is `/HOME/go`.

There are three subdirectory in `GOPATH`:

> `src` -- In **src**, every subdirectory is a package. Source code files are stored in package.
> `pkg` -- When compilation is done, GOLANG will creat a result file in here.
> `bin` -- A folder full of generated executable file.

---

## Usage

### Naming Rule命名规则

#### 变量命名



#### 常量命名

所有字母都要大写

### Main

用于声明一个文件是主文件main，即这个项目starts from here。

> main文件在教学中又被称为：命令源码文件。

```Go
package main

func main(){
    // 主函数内容
}
```

### Comment注释

#### **single line comment**

```Go
// single line comment
```

#### **multi line comment**

```Go
/* multi line comment
   You can type within this section */
```

or

```Go
/*
1st line
2nd line
...
*/
```

### Import

**Format:** `import "package name"`

**Example:**

```Go
import "fmt"
```

### Compile编译

使用terminal进入项目文件夹内，运行`go build`命令进行编译。

> `go build`命令具体用法请查看`Command`文档。

### variable变量

#### 变量的定义

变量的定义有两种方法：

* **指定变量类型**

**Format:** 

```Go
var name type
name = value
```

或

```Go
var name type = value
```

**Example:**

```Go
var num1 int   // 变量的定义
num1 = 30      // 变量的赋值

var num2 int = 100
```

* **类型推断Type inference**（由Go去根据值判断变量类型）
 
**Format:** 

```Go
var name = value
```

还可以使用简短定义（或叫简短声明）

> 简短定义方法不能用在全局变量中

```Go
name := value
```

**Example:**

```Go
var num1 = 30

num2 := 100
```

* **多个变量同时定义**

```Go
var a, b, c int
a = 1
b = 2
c = 3
fmt.Println(a, b, c)
```

Or

```Go
// 同一类型
var m, n int = 100, 200
fmt.Println(m, n)

// 不同类型
var n1, f1, s1 = 100, 3.14, "Go"
fmt.Println(n1, f1, s1)

// 集合类型
var (
    studentName = "Lily"
    age = 18
    sex = "female"
)
fmt.Printf("学生姓名：%s，年龄：%d，性别：%s\n", studentName, age, sex)
```

#### 变量的调用



#### 全局变量

<br>

---

### constant常量

#### 常量的定义

常量命名约定俗成要全部大写。

**Format:** `const identifier [type] = value`

* 显式类型定义： `const b string = "abc"`
* 隐式类型定义： `const b = "abc"`
