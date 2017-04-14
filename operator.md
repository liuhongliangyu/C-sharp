# 运算符

## 运算符概述

我们之前说过，C#程序的运行离不开运算。进一步讲，运算肯定又离不开运算符，因为只有运算符我们才知道应该如何进去运算。在C#中存在很多种运算，为了方便大家记忆和使用，我们队C#的运算符进行了分类。

在C#中的运算符大概分为以下几类：
* 算数运算符
* 赋值运算符
* 比较运算符
* 逻辑运算符
* 三元运算符
* 位运算

## 算数运算符
算数运算符主要作用是对一些数值进行进本运算。

![](http://nts.newbieol.com/static/k30/unity_csharp/5,%E8%BF%90%E7%AE%97%E7%AC%A6/images/1.png)

```C#
+ 加号、字符串连接符
- 减号
* 乘号
/ 除号
% 取余（摸）
++ 自增
-- 自减
```

**C#中用两个整数做除法运算时，最终的结果永远是整数，无法得到小数。**

```C#
class Demo
{
  public static void Main(string[] args)
  {
    System.Console.WriteLine(6234 / 1000 * 1000);
  }
}
```
最后结果是6000。因为6234和1000都是整数int型他们做除法不会得到小数型6.234而是得到int型6.**注：不是四舍五入而是直接舍掉小数。**

**加号还有另外的功能叫字符串连接符，可以将两个字符串或者一个字符串和数据连接成一个更大的字符串。**

* %摸是得到两个数值做除法运算后的余数。

```C#
class Demo
{
  public static void Main(string[] args)
  {
    System.Console.WriteLine(5 % 2); //商2余1
      System.Console.WriteLine(2 % 5); //商0余2
      //任何数摸2，结果不是0就是1
  }
}
```
* ++ 自增实在原有的数据基础上加1后在赋值给原有的数据，符号放在数据的前后均可。
```C#
class Demo
{
  public static void Main(string[] args)
  {
    int a = 2;
    //a++;
    //++a;   //等价于 a = a + 1; 对于只有自增运算的表达式来说，自增放到前面后面都一样。
    //System.Console.WriteLine(a);
    //int b = a++;  //运算的优先级，当自增运算符在后面时，先赋值，b = a = 2, 然后再自增a = a + 1 = 3;
    int b = ++a;   //运算的优先级，当自增在前面时，先自增a = a + 1 = 3,然后再赋值b = a = 3;
    System.Console.WriteLine("a = {0}, b = {1}", a, b);
  }
}
```
* 同理自减（--）也是一样，如果只有自减，则前后都一样；如果有其他运算，则要考虑自减运算符在数据的前面还是后面。

## 赋值运算符
赋值运算符顾名思义，它的作用就是赋值。
![](http://nts.newbieol.com/static/k30/unity_csharp/5,%E8%BF%90%E7%AE%97%E7%AC%A6/images/2.png)

```C#
 =   将右边的值赋值给左边的变量
 +=  将左右两边的数值相加再赋值给左边
 -=  将左右两边的数值相减再赋值给左边
 *=  将左右两边的数值相乘再赋值给左边
 /=  将左右两边的数值相除再赋值给左边
 %=  将左右两边的数值求模再赋值给左边
```
* 对于赋值的顺序大家一定要清楚，是从右边向左边赋值。

## 比较运算符
比较运算符的作用是用于比较两边数据的大小及相等。
![](http://nts.newbieol.com/static/k30/unity_csharp/5,%E8%BF%90%E7%AE%97%E7%AC%A6/images/3.png)

```C#
 >   比较左边的值是否大于右边的值
 <   比较左边的值是否小于右边的值
 >=  比较左边的值是否大于等于右边的值
 <=  比较左边的值是否小于等于右边的值
 ==  比较左右两边的值是否相等
 !=  比较左右两边的值是否不等
```
```C#
class Demo
{
  public static void Main(string[] args)
  {
    System.Console.WriteLine(3 > 4); 
    System.Console.WriteLine(3 < 4); 
    System.Console.WriteLine(3 == 4); 
    System.Console.WriteLine(3 >= 4); 
    System.Console.WriteLine(4 <= 4);
  }
}

输出结果一次是:False、True、False、False、True
```

对于比较运算符，我们发现最后的结果要么是’是’，要么是’否’，在C#中我们用布尔类型的值来表示’是’、‘否’，即’是’可以用true表示，‘否’可以用false表示。所以，通过比较运算符运算后得到的结果一定是布尔值（bool）。

## 逻辑运算符

逻辑运算符是用来连接两个布尔值（或结果是布尔值的表达式）的，它可以将两个布尔值进行运算。逻辑运算符包括：
![](http://nts.newbieol.com/static/k30/unity_csharp/5,%E8%BF%90%E7%AE%97%E7%AC%A6/images/4.png)

```C#
class Demo
{
  public static void Main(string[] args)
  {
    int x = 4;
    System.Console.WriteLine(x > 3 & x < 5);// true
    System.Console.WriteLine(x < 3 & x < 5);//false
    System.Console.WriteLine(x < 3 & x > 5);//false
    
    //System.Console.WriteLine(true & false); 这样写也可以
    System.Console.WriteLine(!true);//false
    System.Console.WriteLine(!!true);//true
  }
}

逻辑与&：true & true = true,true & false = false, false & true = false, false & false = false
逻辑非!：非真即假，非假即真
```
* 注意：&和&&、|和||的区别：&&运算符进行运算时，如果运算符左边为false，那么右边无论是true还是false都不予计算，直接得出结果为false；||运算符进行运算时，如果运算符左边true，那么右边无论是true还是false都不予计算，直接得出结果为true。以上效果都可以叫做短路效果。

## 三元运算符（三目运算符）
三元运算符又可以叫三目运算符，表示三个元素参与运算的符号。三元运算符只有一种。
![](http://nts.newbieol.com/static/k30/unity_csharp/5,%E8%BF%90%E7%AE%97%E7%AC%A6/images/5.png)

三元运算符的使用格式：条件表达式 ? 数据1 : 数据2

```C#
class OpeDemo5
{
  public static void Main(string[] args)
  {
    //int a = (3 > 4) ? 100 : 200;//冒号两边可以是具体数据
    //System.Console.WriteLine(a);
    
    bool a = (3 > 4) ? (3 > 4) : (3 < 4);//冒号两边可以是表达式，但要明确表达式结果的类型
    System.Console.WriteLine(a);//结果为true
  }
}
```
* 其中，条件表达式就是结果为布尔值的表达式。

## 位运算符
位运算符主要是针对二进制运算的，包括：
![](http://nts.newbieol.com/static/k30/unity_csharp/5,%E8%BF%90%E7%AE%97%E7%AC%A6/images/6.png)

```C#
 &    与运算  (只有全是真时才得到真)
 |    或运算  （只要有一个真即为真）
 ^    异或运算 （只要有一真一假即为真，全真或全假都是假）
 <<    左位移
 >>    右位移
 ~    取反
```
* 讲一个数左移几位，就是这个数乘以2 的几次方。例如：3 << 2 = 3 * 2 * 2 = 12; 




