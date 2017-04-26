# 字符串的常见特征及处理

C#中字符要用单引号标识，为char类型，比如 ‘a’, ‘5’, ‘!’等。单引号中能且仅能放一个字符。

字符串属于引用数据类型，用双引号标识，但大多数对于字符串的使用和值类型比较像：
```C#
class StringOpeDemo
{
  public static void Main(string[] args)
  {
    char ch = 'a';
    string str = "hello";
  }
}
值类型和string类型的变量的声明格式类似。

```
单个字符也可以用双引号标识起来，依旧表示为字符串，还可以有长度为0的字符串，表示为：""（双引号中什么都没有）
```C#
class StringOpeDemo
{
  public static void Main(string[] args)
  {
    string ch = "a";  //单个字符用双引号标识，也是字符串
    string str = "";  //长度为0的字符串
  }
}

```
字符串是由一个个的字符连接起来的，可以看作是字符组成的数组。所以字符串中有Length属性，表示这个字符串的长度，也就是字符的个数。
```C#
class Demo
{
  public static void Main(string[] args)
  {
    string str = "hello world";   //str可以看作是一个由字符组成的数组
    Console.WriteLine(str.Length);  //打印结果为11，即str的长度为11，里面一共有11个字符（包括空格）

    char ch = str[1];   //把数组中索引为1的字符取出。
    Console.WriteLine(ch);    //打印 字符为 'e'

    /*遍历一个字符串中的每一个字符*/
    for(int i = 0; i < str.Length; i++)
    {
      System.Console.WriteLine(str[i]);//依次输出字符串中的内容
    }
  }
}

```
字符串有一个重要的特性，不可变性。也就是说，字符串一旦声明后就不可以被改变。有的同学可能已经想到类似于这样的代码：
```C#
class Demo
{
  public static void Main(string[] args)
  {
    string str = "abc";
    str = "nba";
    //str明明变化了！从"abc"变成了"nba"！
  }
}

```
确实，从代码的表面来看确实变化了，但实际上真的没变。那是因为字符串string是引用数据类型，每当创建一个字符串的时候都会在内存中开辟空间分配地址创建一个字符串对象，然后将这个对象的地址值赋值给变量。当我们重新创建一个字符串的时候，在代码上看是将字符串赋值给相同的变量，实际上是将新字符串的地址值赋值给了变量。也就是说，同一个str变量先后两次被两个不同字符串的地址值赋值。变的只是该变量所引用的地址值，而字符串本身在内存中确确实实是没有变化的，是两个独立的字符串。这就是字符串的不可变性，一旦声明了一个字符串，它将无法被改变。

引用类型简单讲，引用的是数据的地址值，而不是数据本身；只有值类型才是直接将值赋值给变量本身。

## String类详解

String类封装了大量的属性和方法可以对字符串进行操作，接下来介绍一下常用的内容。

常用属性：

Length  获取当前 String 对象中的字符数。

常用方法：
```C#
ToLower()   得到字符串的小写形式。
ToUpper()   得到字符串的大写形式.
Trim()      去掉字符串两端的空白。
Replace(string oldValue, string newValue)   将字符串中的出现oldValue的地方替换为newValue
Substring(int startIndex)   取从位置startIndex开始一直到最后的子字符串
Substring(int startIndex, int length)   取从位置startIndex开始长度为length的子字符串
Contains(string value)    判断字符串中是否含有子串value
StartsWith(string value)  判断字符串是否以子串value开始
EndsWith (string value)   判断字符串是否以子串value结束
IndexOf(string value)     取子串value第一次出现的位置
IsNullOrEnmpty(string)    静态方法，判断是否为空或长度为0 的字符串（null和""）
Equals(string, StringComparison.OrdinalIgnoreCase)    两个字符串进行不区分大小写的比较
Split(params char[] separator) //此方法是传入数组型参数，后期会将
Split(char[] separator, StringSplitOptions options) //StringSplitOptions枚举中有备选项，可以选择以什么样的方式进行分割
Split(string[] separator, StringSplitOptions options)
```
* 注意，String类中的所有对于字符串操作的方法，本质上不是操作的字符串本身，而是重新创建了一个新的操作后的字符串。

String使用举例：
```C#
class StringOpeDemo
{
  public static void Main(string[] args)
  {
    //得到字符串的小写形式
    string str = "HELLO";
    string s = str.ToLower();
    System.Console.WriteLine(s);//输出hello

    string str1 = "www.baidu.com";
    string s1 = str.Substring(4, 5);//截取从索引4开始后5个字符的子字符串
    System.Console.WriteLine(s1);//输出baidu
  }
}

请同学先按照自己的想法把以上内容自己写代码实验结果，然后再看示例代码。
```
## StringBuilder类详解

StringBuilder类同样是对字符串操作的类，它提供的是专门对字符串进行增删查改的操作，也就是说，通过StringBuilder创建的字符串是可以被修改的，这也是StringBuilder和String的区别。

String本身是表示不可变的字符串类型，而StringBuilder表示可变的字符串类型。

接下来介绍一下StringBuilder里的常见内容：

常见属性：
* Length   	  获取或设置当前 StringBuilder 对象的长度
* Capacity    获取或设置可包含在当前实例所分配的最大字符数

构造函数：
* StringBuilder(String)，使用指定的字符串初始化 StringBuilder 类的新实例。
* StringBuilder(String, Int32), 用指定的字符串和容量初始化 StringBuilder 类的新实例。

常见方法：
* Append(String)          添加。将指定字符串追加到当前StringBuilder的结尾。
* Insert(Int32, String)   插入。将字符串或对象插入到当前StringBuilder对象的指定索引处。
* Remove(Int32, Int32)    移除。从当前StringBuilder中移除指定数量的字符
* Replace(String, String) 替换。将当前字符串中出现的所有指定字符串的替换为其他指定字符串

StringBuilder中的方法大多数都是对字符串进行增删查改的方法，以上只列出了4个代表性方法，其中还包括各自的多个重载方法，大家应该自行实验测试，然后再看示例代码。

StringBuilder的声明：
```C#
using System.Text   //使用StringBuilder需要单独引用其所在的命名空间

class Demo
{
  public static void Main(string[] args)
  {
    //声明StringBuilder对象方式1：无参构造函数，表示只有该对象的容器，里面没有具体字符串，可以通过Append()方法进行添加
    StringBuilder sb1 = new StringBuilder();
    Console.WriteLine(sb1.Length);  //字符串长度为0
    Console.WriteLine(sb1.Capacity);    //默认容量为多少呢？

    //声明StringBuilder对象方式2：带参构造函数，直接声明了可变字符串
    StringBuilder sb2 = new StringBuilder("hello world");
    Console.WriteLine(sb1.Length);  //字符串长度为11
    Console.WriteLine(sb1.Capacity);    //容量和sb1一样吗？
    }
}
```
String和StringBuilder的区别

到现在，我们发现String和StringBuilder都提供了对字符串的操作，而StringBuilder更加倾向于对字符串的增删查改，而String基本没有，所以这两个类的区别到底是什么呢？

其实很简单，我们在之前也提到了。String就是代表内存中无法被改变的字符串，即不可变性。而StringBuilder提供的则是可变字符串，这就是两个类的区别。

注意，大写的String和小写的string没有区别，两者可以完全互换。

对于String类，我们可以这样：
```C#
class Demo
{
  public static void Main(string[] args)
  {
    string str1 = "hello";
    string str2 = "world";
    str2 = str1 + str2;
    Console.WriteLine(str2);   //结果为helloworld
  }
}
```
表面上看似是str2的“world”直接追加到str1的“hello”后面，但实际上是在内存中又创建了一个字符串对象为helloworld，也就是说，短短3行代码就在内存中创建了3个对象。如果我们持续的对同一个String字符串做类似的操作，每一次都要重新创建一个对象，如果操作过多，消耗内存，降低效率，这就是不可变性。所以我们可以使用StringBuilder来创建修改频繁的字符串：
```C#
class Demo
{
  public static void Main(string[] args)
  {
    //如果想使用可变字符串，要先找StringBuilder，向使用它，先创建对象。
    StringBuilder sb = new StringBuilder();
    StringBuilder sb2 = new StringBuilder();//可以创建多个StringBuilder对象

    System.Console.WriteLine(sb.Capacity);//StringBuilder默认可以存储16个字符
    System.Console.WriteLine(sb.Length);//没有字符为0
    System.Console.WriteLine("----------------");
	
    sb.Append("good");//使用Append方法向sb中添加字符串
    System.Console.WriteLine(sb.Length);//长度为4
    System.Console.WriteLine(sb);//打印出该字符串
    System.Console.WriteLine("----------------");

    sb.Append("morning,吃饭了吗，嘿嘿");//添加字符串
    System.Console.WriteLine(sb.Length);//打印19，为当前是19个字符
    System.Console.WriteLine(sb.Capacity);//打印32，如果超出StringBuilder的范文，则可以自动成倍扩容
    System.Console.WriteLine(sb);//打印最终的字符串
  }
}
```
这就是String和StringBuilder的区别，不可变性字符串和可变性字符串。
