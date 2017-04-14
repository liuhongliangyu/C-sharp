# 流程控制

流程控制分为：分支结构和循环结构。

## 分支结构

分支结构分为：判断结构和选择结构。

### 判断结构

#### if语句的三种形式

第一种格式：
```C#
if (条件表达式)
{
  执行语句；
}
``` 
```C#
class IfDemo
{
  public static void Main(string[] args)
  {
    int a = 3;
    if (a < 4)
    {
      System.Console.WriteLine("OK");
    }
    System.Console.WriteLine("ole");
  }
}
结果为OK ole
```

第二种格式：
```C#
if(条件表达式)
{
  执行语句；
}
else
{
  执行语句；
}
```
在第二种格式中，无论条件表达式的结果是什么，至少会有一条语句被执行。

第三种格式：
```C#
if(条件表达式)
{
  执行语句;
}
else if(条件表达式)
{
  执行语句；
}
.
.
else
{
  执行语句；
}
```

```C#
class IfDemo
{
  public static void Main(string[] args)
  {
    int a = 3;
    if (a > 1)
    {
      System.Console.WriteLine("A");
    }
    else if (a > 2)
    {
      System.Console.WriteLine("B");
    }
    else if(a > 3)
    {
      System.Console.WriteLine("C");
    }
    else 
    {
      System.Console.WriteLine("D");
    }
  }
}

结果为A
```

