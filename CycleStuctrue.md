# 流程控制：循环结构
循环结构：重复，可以帮助我们重复执行某些动作（代码、命令）
* while循环
* do..whil循环
* for循环
* **一般情况下，循环需要2个必要条件：
1. 循环条件。
2. 循环次数。**
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
    for(int a = 1; a < 3; a++)
    {
      for(int b = 1; b < 4; b++)
      {
        System.Console.WriteLine("hello");
      }
    }
    //结果是打印6个hello
  }
}
```
## foeeach循环语句格式：（后面学习）
```C#
foreach(数据类型 数据名 in 容器名)
{
  执行语句;
}

需要注意的是foreach语句只能用来遍历。
```
* **while能做的，for也能做，do..while也能做。**
* 

























