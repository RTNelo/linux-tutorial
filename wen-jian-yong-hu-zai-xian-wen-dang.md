# 文件 / 用户 / 手册

## 一种认识 Linux 操作系统（服务）的方式

* 了解这些系统程序 / 指令（System Program）是如何使用的
* 学习系统调用（System Call）
* 编写自己的系统程序

## 文件 / File

在 Linux 操作系统里，**“一切都是文件”**。而文件的“打开”等状态，是用**文件描述符**表示的。

> #### 自驱式学习
>
> Linux 提供了完善且清晰的**用户手册**（Manual），可以帮助我们自驱地学习如何使用该操作系统。我们可以使用指令在 Manual 中进行关键字搜索，以获取我们需要的指令及语法。
>
> 我们可以使用`man <name>` 查询某个指令 / API 的手册，同时可以使用`man man`获取 Linux Manual 更详细的用法。
>
> **注意：Server 版本的 Linux 发行版中，出于空间资源的考虑，系统默认删除了很多详尽的说明或者不常用的指令文档，所以请尽量使用 Desktop 版本进行 Linux 学习。**

### 如何解决“如何打开文件”这个问题？

尝试使用 Linux Manual 进行搜索：`man -k file | grep open | grep \(2\)`。该指令的含义是：在 Manual 中搜索 file 关键词，并过滤保留包含 open 的条目，再次过滤保留包含 \(2\) 的条目（即 Manual 的第二章）

> 管道（Pipe）：`|`符号，又称管道操作符，它的功能是将它左边程序输出的内容输入到右边的程序中，即为左右两个程序建立一个“管道”，实现 I/O Redirection。

### 在终端中浏览大量内容

在传统的 UNIX 操作系统环境中，由于缺少 GUI ，只能显示一个屏幕大小的文本内容。为了解决这个问题，Linux 提供了诸如 `less`，`more`等辅助显示大量文本的工具。通过与`|`配合可以很轻松地在屏幕范围内浏览大量文本。

`less`和`more`都是用来浏览无法在一个屏幕显示完全的大文件的工具。`more`是一个很古老的指令，顾名思义，他只能“more”，即只支持向下翻页。与`more`不同的是，`less`不仅可以向下翻页，同时也可以向上翻页。不过，很多现代的 Linux 发行版在执行`more`指令的时候自动执行`less`，或是提供了一个更接近`less`的`more`以方便用户使用。

_相关链接：_[_https://unix.stackexchange.com/questions/81129/what-are-the-differences-between-most-more-and-less_](https://unix.stackexchange.com/questions/81129/what-are-the-differences-between-most-more-and-less)

### 编程：仿写 cat 指令

#### 语言提示：参数列表

相信很多学过 C 语言的同学，都见过如下代码：

`int main ()`

但实际上，main 函数的完整原型是这样的：

`int main (int argc, char* argv[])`

`argc`是 argument counts 的缩写，表示该可执行程序收到的参数个数，`argv`是 argument value的缩写，是收到的参数构成的数组列表。

\[WIP\]

##### 参数是如何传递到程序中的？

在 Linux 中，“万物皆文件”，指令也不例外。我们在执行某个指令的时候，其实是在执行这个指令对应的可执行文件（或者脚本）。在执行有些指令，比如 cp（复制）指令时，我们会在后边添加一些额外的内容，并用空格分隔开，比如`cp -r ~/Desktop/test-folder ~/Documents/`，那些用空格分隔开的就是程序的参数，也就是`argv`。

### 编程：仿写 cp 指令

#### 语言提示：buffer

buffer（缓冲区）

buffer的大小会影响二进制流传递的效率。

### 初窥 Linux 文件系统

\[Access Control Lists 权限控制列表\]

### 文件操作及系统调用

#### 文件操作

对于一个文件的操作，无外乎以下四种：打开、关闭、写入、读取。Linux Manual 给出了非常清晰的关于文件 open / close / write / read 操作的文档说明，不妨使用上边提到的`man -k`尝试搜索一下。我们也会在下边的编程练习中给出提示。

#### 系统调用

文件在 Linux 操作系统中**非常重要。**在 Linux 中，设备I/O、SOCKET等一系列操作归根结底都是在进行文件操作。因此文件状态也同样至关重要。回到我们最先提到的概念：在 Linux 系统中，文件的“打开状态”等一系列状态都是通过文件描述符表示的。而**系统是如何描述一个文件的呢？**

#### 文件描述 / File Description

## 用户 / User

### 思考：系统如何表示“一个用户登录了”？

#### 从指令出发

Linux 为我们提供了一个指令，用来查看当前在线的用户列表：`who`。它是怎么实现的呢？不妨先在 Manual 里边看一看：

`man who`

如果你的 Linux 拥有完整的 Manual ，你应该会看到如下片段：

\[WIP: If file is not specified, use /var/run/utmp\]

### 编程：仿写 who 指令

## 手册 / Manual



