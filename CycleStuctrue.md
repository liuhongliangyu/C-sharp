# 流程控制：循环结构
循环结构：重复，可以帮助我们重复执行某些动作（代码、命令）
* while循环
* do..whil循环
* for循环
* **一般情况下，循环需要2个必要条件：**
1. 循环条件。
2. 循环次数。
## while循环语句格式
```C#
while(条件表达式)
{
  循环体;
}

```
代码举例：
```C#
class WhileDemo
{
  public static void Main(string[] args)
  {
    int a = 1;

    while(a < 3)	//是否循环要看条件表达式的最后结果
    {
      System.Console.WriteLine("hello world");
      a++; //使用自增符号表示a的增量
    }
    System.Console.WriteLine("haha");
  }
}
结果为2次hello world和1次haha
```
## do .. while循环语句格式：
```C#
do
{
  循环体;
}
while(条件表达式);

注意和while的区别。
```
代码示例：
```C#
class WhileDemo
{
  public static void Main(string[] args)
  {
    int a = 3;
		
    do
    {
      a++;
      System.Console.WriteLine("hello");
    }
    while(a < 3);
  }
}
结果为2次hello
```
## for循环语句格式
```C#
for(初始化表达式; 条件表达式; 循环后的操作表达式)
{
  循环体;
}
```
代码示例：
```C#
class WhileDemo
{
  public static void Main(string[] args)
  {
    for(int a = 1; a < 3; a++)
    {
      System.Console.WriteLine("hello");
    }
  }
}
```
## for循环中存在一种特殊的格式循环嵌套：
```C#
for(初始化表达式; 条件表达式; 循环后的操作表达式)
{
  for(初始化表达式; 条件表达式; 循环后的操作表达式)
  {
    执行语句;
  }
}
```
代码示例：
```C#
class ForDemo
{
  public static void Main(string[] args)
  {
    for(int a = 1; a < 3; a++)          //外循环
    {
      for(int b = 1; b < 4; b++)       //内循环
      {
        System.Console.WriteLine("hello");
      }
    }
    //结果是打印6个hello
  }
}

```
**每执行一次外循环，就执行全部的内循环。**
## foeeach循环语句格式：（后面学习）
```C#
foreach(数据类型 数据名 in 容器名)
{
  执行语句;
}

需要注意的是foreach语句只能用来遍历。
```
* **while能做的，for也能做，do..while也能做。但是for用的比较多**
* 无限循环格式：
```C#
while(true)
{
   执行语句；
}
for（; ;）
{
  执行语句；
}
```
## break关键字
**break，跳出，应用于循环结构和选择结构。作用是跳出所在的循环并终止所在循环。

```C#
class ForDemo
{
  public static void Main(string[] args)
  {
    for(int a = 1; a < 3; a++)
    {
      System.Console.WriteLine("hello");

      if(a == 1)
      {
        break;
      }
    }
  }
}
结果为打印1次hello
```
* 一般需结合循环、判断语句，只跳出所在循环。
```C#
class ForDemo
{
  public static void Main(string[] args)
  {
    for(int a = 1; a < 3; a++)
    {
      for(int b = 1; b < 4; b++)
      {
        System.Console.WriteLine("11111");
        break;
      }
    }
  }
}
break只会跳出它所在的循环
```
## continue关键字
continue，继续，应用于循环结构。作用是结束本次循环继续执行下一次循环。
```C#
class WhileDemo
{
  public static void Main(string[] args)
  {
    for(int a = 1; a <= 11; a++)
    {
      if(a % 2 == 0)
      {
        continue;
      }
      else
      {
        System.Console.WriteLine(a);
      }
    }
  }
}
结果为打印出1~11之间所有的奇数
```
continue正常情况下和分支结构结合使用，一般不单独使用

**注意，break和continue都是关键字，同时也都可以单独成句。如果这两个语句离开了应用范围将没有意义
* 如果将continue放在循环语句最后，那么写与不写continue都一样。


























