# C#
## 第一讲
### C#语言简介
* C#是一个现代的、通用的、面向对象的编程语言，他是有微软（Microsoft）开发的，有Ecma和ISO核准认证的
* C#是由Anders Hejlsberg（安德斯.海尔斯伯格）和他的团队在.Net框架开发期间开发的。
* C#是专为公共语言基础结构（CLI）设计的。CLI有可执行代码和运行时环境组成，允许在不同的计算机平台和结构上使用各种高级语言。
C#由来：C#是由微软（Microsoft）在2000年发布的一种新的面相对对象（思想）语言，由安德斯.海尔斯伯格主持开发的，最初叫Cool，后来叫C#。
### 人机交互方式
1. 图形化界面（Graphical User Interface GUI）:简单直观容易接受，容易上手操作。
1. 命令行方式（Command Line Interface CLI）:需要有控制台，输入特定的指令让计算机完成操作。
    * 麻烦，需要记住命令.
### C#运行环境简介
在Windows中，C#的运行环境存在于 C:\Windows\Microsoft.NET 下。其中，C# 的语言编译器存在于C:\Windows\Microsoft.NET\Framework64\v4.0.30319（或v3.5）中。
C# 的语言编译器为csc.exe这个文件，我们可以在dos命令行中打开这个文件对C# 原文件进行编译。
* 注：v （version）是编译器版本。

找到csc.exe工具(csc.exe是C#语言的编译器)。编译器(compiler)(c sharp compiler)作用：
1. 计算机不认识我们写的代码，编译器可以将C#代码编译成计算机底层能识别的二进制，以便计算机识别。
1. 查错！

### 常用dos命令
```
dir 列出当前目录下的文件和文件夹 directory目录
md 创建目录 make directory
cd 进入指定目录 change directory
cd.. 退回到上一级目录
cd\ 直接回到根目录
rd 删除目录 remove directory
del 删除文件
exit 退出dos命令行
help 寻求帮助
ipconfig 获取当前主机的ip
```

### 环境变量的配置
环境变量可以帮助我们在任何目录下都能够使用dos来调用C#的编译器，省去了输入深层次目录的烦恼。

环境变量的配置：
右键“我的电脑” -> 属性 -> 高级系统设置 -> 环境变量 -> 系统变量 -> Path

我们只需要把csc.exe文件所在的目录粘贴到变量值里面就可以，注意用‘;’和其他路径分开。

### 类的简单介绍
一个 C# 程序主要包括以下部分：
* 命名空间声明（Namespace declaration）
* class (类)
* Main 函数
* 字段(或变量)
* 属性
* 函数
* 语句（Statements）& 表达式（Expressions）
* 注释

### “Hello World”实例
* 注意代码格式。
C#代码是以 类 的形式去体现的。类：可以简单理解为装C#代码的地方，类是C#代码中最根本的结构。
1. 编辑：写代码。
1. 编译：翻译代码。命名文件时要用‘.cs’。
1. 运行：在文件所在目录下，'csc.exe 文件名.cs'，生成'文件名.exe',执行‘文件名.exe’。
```
需求：实现功能，可以在控制台上打印“Hello World”
分析：
1. 需要写C#代码
2. 代码以什么结构为基础？类！
3. 如何定义一个类？ class！
4. class要有自己的名字和范围
5. 需要有Main函数使程序运行
6. 在Main函数中写上打印语句。如System.Console.WriteLine("Hello World");
```
### 补充说明
* Main(主函数)的作用：一个程序必须要有一个Main函数，因为Main函数是一个程序的入口。
* 符号：分号代表一句话的结束。注：结构语句不需要分号，用大括号；执行语句用分号。
* 大小写：C#严格区分大小写，缩进格式。

### 注释的运用
1. 单行注释：只能注释一行到回车处。‘//’
1. 多行注释：可以对多行文字进行注释。‘/*        */’
* 注释的作用：
1. 注解说明程序的文字。
1. 用来调试程序。
1. 写程序规范，方便查看。

### 标识符
* 定义：程序中自定义的名字。（没有具体的定义）
* 使用规范：
1. 组成：26个英文字母大小写、0-9数字即下划线组成。
1. 注意事项：不能使用C#中的关键字，不能数字开头。
1. 规范：单词首字母大写，要写有意义的标识符。

### 关键字
* 定义：被C#语言赋予了特殊含义的单词，C#中共有近100个关键字。
* 举例:class(表示一个类的创建)，static，void，Main，string，args，System，Console，WriteLine，ReadLine，Write，Read