## 数据类型
### 数据类型的由来
在我们的日常生活中存在着各种各样的数据，我们可以把每一种数据根据它们的特点进行归类划分成很多种类，从而成为不同的数据类型。比如，整数，小数…

C#也一样。只要程序运行就离不开数据的运算，所以每一种数据也一定要有分类。在C#中对于数据类型的分类比较严格，从而C#也可以叫做强类型语言。

### 数据类型的分类
C#中数据类型总的来说可分为两大类，值类型和引用类型。

值类型包括：整型，浮点型，字符型(char)，布尔型(bool)，枚举型(enum)，结构型(struct)。其中，整型又包含8种分别为：byte,sbyte,short,ushort,int,uint,long,ulong；浮点型又包括3种分别为：float,double,decimal。

引用类型包括：类类型(class)，字符串类型(string)，接口类型(interface)，委托类型(delegate)

我们可以用结构图来表示一下：

![](http://nts.newbieol.com/static/k30/unity_csharp/2,%E6%95%B0%E6%8D%AE%E7%B1%BB%E5%9E%8B/images/01.png)

* 注意：上述类型中的英文都是C#系统保留的关键字，大家可以在今后的学习中不断练习记忆，而没有必要现在就全记住。对于目前阶段，我们比较常用的是值类型以及字符串类型。

### 数据类型详解
* 整形

整型是常用的数据类型，表示整数，可以分为8种。如下图：
![](http://nts.newbieol.com/static/k30/unity_csharp/2,%E6%95%B0%E6%8D%AE%E7%B1%BB%E5%9E%8B/images/02.png)

在这8种整型中，我们发现每一种类型都有它自己的取值范围，比如sbyte类型的取值范围只能是 -128 ~ 127 之间，无法取到这个区间之外的值。

在整型的8种数据类型中，为了方便记忆可以两两一对（sbyte和byte，short和ushort，int和uint，long和ulong）。每一对有一个区别是“有无符号”，有符号就是有负号，无符号就是没有负号，每一对虽然有这样的区别但是它们之间的跨度是一样的，无符号的都是从0开始。

字节是计算机中的基本存储单元，计算机中对于任何文件（数据）的存储都是以字节为单位进行的。如图：

![](http://nts.newbieol.com/static/k30/unity_csharp/2,%E6%95%B0%E6%8D%AE%E7%B1%BB%E5%9E%8B/images/03.png)

* 思考：为甚么要把整数分为这么多类型？答：与计算机发展有关，并且可以节省空间。

* 浮点型

浮点型也是常用的数据类型，表示小数。如图：

![](http://nts.newbieol.com/static/k30/unity_csharp/2,%E6%95%B0%E6%8D%AE%E7%B1%BB%E5%9E%8B/images/04.png)

其中，比较常用的是float和double类型，double类型比float类型要更加精确。而decimal类型更加精确，主要用于会计或要求非常精确的运算，不常用。

对于浮点型的取值范围来说由于比较复杂，大家现在可以先不用过多考虑。

在保留位数上，如float为7位，不是说保留小数点后面7为有效数字，而是小数点前后的数字都包括。这一点我们将会在《常量与变量》一课中学习。

* 布尔型（bool）

布尔型比较特殊，只有两个值（true和false），不能有其他的值。
true表示真，false表示假，后面会经常使用。

![](http://nts.newbieol.com/static/k30/unity_csharp/2,%E6%95%B0%E6%8D%AE%E7%B1%BB%E5%9E%8B/images/05.png)

* 字符型

C#中字符型是用单引号标识的，且只能包含一个，比如： 'a' 、'6'，在内存中占用2个字节。

错误字符的表示形式：'abc'、'25'、''

![](http://nts.newbieol.com/static/k30/unity_csharp/2,%E6%95%B0%E6%8D%AE%E7%B1%BB%E5%9E%8B/images/06.png)

以上列出的是比较常用的数据类型的介绍，还有一部分没有介绍，后面会不断学习理解。目前阶段我们先掌握以上类型的使用，具体使用方式会在《常量与变量》课程中学习。

## 常量与变量
### 变量

* 什么是变量？变量就是内存中的一块存储区域，可以不断的存储同一类型的变化的数据。

* 如何定义变量？格式： 数据类型 变量名 = 初始化值

在定义变量的时候，我们就要用到之前学习的数据类型了。

```C#
class Demo
{
  public static void Main(string[] args)
  {
    //定义一个int类型的变量。请问该变量在内存中占用多少字节？
    int number = 10;
    //定义变量后我们可以使用这个变量，打印它，结果为10.
    System.Console.WriteLine(number);
  }
}
```

其中，int 为数据类型，number为我们自定义的变量名，10则是给这个变量的初始化值。那么如何“变”呢？我们可以继续往下写：

```C#
class Demo
{
  public static void Main(string[] args)
  {
    //定义一个int类型的变量。
    int number = 10;
    //使变量改变数值。这样也可以叫做使用这个变量给它重新赋值。请问这里为什么不需要数据类型？
    number = 20;
    //定义变量后我们可以使用这个变量，打印它，结果为20.
    System.Console.WriteLine(number);
  }
}
```
这样number变量里面存储的数据就变成了20。

除了int类型，还有很多其他的类型，大家应该一一尝试并可以做到熟练定义各种类型的变量。代码举例：

```C#
class Demo
{
  public static void Main(string[] args)
  {
    //各种整型变量举例，注意初始化值不能超过其取值范围。
    int number = 10;
    sbyte s = -3;
    short sh = 32766;
    uint ui = 15;
    long lo = 485566842;

    //浮点型变量举例
    float f = 2.523f;  //float类型的变量一定要在初始值后面加上后缀 f，否则会被认为是double类型导致等号左右两边类型不一样而报错。
    double dou = 100.25;  //double类型不需要任何后缀。

    //bool类型变量举例，注意bool类型只有两个值
    bool bo = true;

    //char类型变量举例，注意char类型的特点
    char ch = 'a';
    char c = '8';

    //字符串类型变量举例，注意字符串类型的特点
    string str = "abcdefg";
    string stri = "500";

    //可以把每一个变量的值都打印出来，在这里我们值打印两个，其余的大家自己尝试
    System.Console.WriteLine(bo);
    System.Console.WriteLine(str);
  }
}
```

**注意1：在定义变量的时候，我们必须要明确这个变量的数据类型，来表示这个变量可以存储什么样的数据。**

**注意2：一个变量同一时间只能存储一个数据，当存储第二个的时候之前存储的数据会消失，突出了“变”。**

**注意3：一般情况下，变量定义后要有初始化值（第一次给变量的值）。**

**注意4：变量的初始化值的类型要和定义的数据类型相符，也就是等号左右两边的类型要相等。**

**注意5：浮点型变量在保留位数上有需要注意的地方，比如float为保留7位有效数字，这7位包括小数点前后的数字，举例如下：**

```C#
class Demo
{
  public static void Main(string[] args)
  {
    float f1 = 1234.56789f;
    double d1 = 1234.56789;
    System.Console.WriteLine(f1); //有效数字是7位，结果为1234.568，最后一位小数会四舍五入
    System.Console.WriteLine(d1);  //有效数字是15~16位，都会保留下来。
  }
}
```

* 注意：

错误（error）：程序无法运行，必须要修改代码错误。

和警告（warning）：不影响程序运行，但是最好保证代码没有警告。

### 常量

在日常生活中包含了各式各样的数据，如数字，文字，字母等等。我们可以根据不同数据的不同表现形式将其分类。事实上这些数据可以叫做常量。比如数字1，字母h等等，这些数据出现后不会被改变，就是常量。而在刚刚学过的变量中，如int number = 10，number就是变量，10则是常量。

在C#中我们可以自定义值无法被改变的常量，格式如下：
* const 数据类型 名称 = 初始化值

```C#
class Demo
{
  public static void Main(string[] args)
  {
    //定义常量，使用const关键字
    const int num = 10;
    num = 20; //这时会报错，提示常量无法被改变。在其他程序中也无法改变这个num的值。
  }
}
```

* 其中const是关键字，表示值不可改变。

**注意：不可改变是指在程序运行的过程中无法被程序所改变。**

### 标识符命名规范

标识符：程序中自定义的名称。

我们在写程序的时候经常会用到自定义名称，比如：类名，变量名，函数名等，这些名字有统一的称呼叫做标识符。

在定义标识符时我们要遵循几个规范：
* 1，不能以数字开头
* 2，只能包含：26个英文字母大小写，0-9共10个数字，以及符号下划线 _
* 3，不能使用关键字
* 4，名字要有意义，要和当前定义的内容有所对应，多个单词首字母大写
* 5，C#中严格区分大小写
* 6，类名和文件名一定要一致

常见的不规范或错误的标识符：
abc、123、1bc、Hello!、等等，如果标识符中要带符号，只能是下划线，不能包括其他的符号。

正确的标识符：
Hello、Hello_World、HelloWorld、Demo1

## 类型转换
### 类型转换的原因

在一般情况下，只有数据类型相同的数据才可以进行运算。比如在日常生活中，我们的汉字可以作为一种数据，而数字也可以，通常我们没有办法把这两种数据进行计算。

在程序运行过程中一定少不了数据的运算，而由于数据的类型多样，也经常会遇到需要运算的数据类型不一致，这时候就会出现类型转换，将数据类型转换成一致，也就是类型转换。

### 自动类型提升
```C#
class Demo
{
  public static void Main(string[] args)
  {
    int a = 3;  //int类型
    sbyte b = 4;  //sbyte类型
    int c = a + b;  //将两种类型的数据相加后的和赋值给int类型的c变量
    Console.WriteLine(c); //打印两个数据的和为7
  }
}
```

在上述例子中，变量a和c为int类型占4字节，b为sbyte类型占1字节。实际当a和b做运算时，b会自动把类型提升为int类型从而使两边类型一致。最后算出来的结果为7也是int类型，才可以赋值给变量c。我们可以发现上述例子中并没有写一些特定的代码就进行了类型转换，而且是系统底层自动帮我们完成的，所以我们可以叫做自动类型提升（隐式转换）。

常见情况下自动类型提升的几种情况可能：
* 所有的sbyte、byte、short、ushort和char都将默认被提升到int类型
* 如果数据有long类型，计算结果就是long类型
* 如果数据有浮点型类型，计算结果为浮点型类型
* 如果数据有double和float类型，计算结果就是double类型

**注意：C#中，整数默认为int类型，小数默认为double类型。所以字节数比int低的整型和字节数比double低的浮点型都会自动类型提升到默认类型。**

### 强制类型转换

```C#
class Demo
{
  public static void Main(string[] args)
  {
    int a = 3;  //int类型
    sbyte b = 4;  //sbyte类型
    sbyte c = a + b;  //将两种类型数据相加后的和赋值给sbyte类型的c变量，这时会报错。
  }
}
```
在上述例子中，变量a为int类型占4字节，b和c为sbyte类型占1字节。实际当a和b做运算时，b会自动类型提升为int类型，使得最后结果为int类型。可是变量c的类型与最后结果的类型不统一，无法将占用4字节的int类型7赋值给占用1字节的sbyte类型c，所以代码会直接报错。如何解决呢？我们可以使用强制类型转换，如下：

```C#
class Demo
{
  public static void Main(string[] args)
  {
    int a = 3;  //int类型
    sbyte b = 4;  //sbyte类型
    sbyte c = (sbyte)(a + b); //这就是强制类型转换，将a和b的和转换为sbyte类型，并赋值给sbyte类型的c变量，注意书写格式。
  }
}
```
这就是做了强制类型转换的代码。我们需要把最后的结果进行强制转换，所以a和b要使用小括号括起来。前面的(sbyte)表示要转换为什么类型。强制转换有可能涉及到精度丢失。

注意，目前的类型转换中大部分是值类型的转换，后期我们还会学习引用类型的转换，写法上没有太大区别。

### 字符类型运算

```C#
class Demo
{
  public static void Main(string[] args)
  {	
	/*
	char ch = 'a';
	System.Console.WriteLine(ch);
	System.Console.WriteLine(ch + 1);*/
	
	char ch = '中';		//因为C#中使用Unicode码表，所以可以使用中文
	System.Console.WriteLine(ch + 0);//中字在Unicode中所对应的十进制数字，可以转换成二进制。
  }
}
```
ASCII中，字符a对应97，字符A对应65。

C# 中使用的是Unicode码表。当字符型数据参与数值型运算时，会自动转换为码表中所对应的数值。

### 字符串与变量结合输出及占位符

```C#
class OutputDemo
{
  public static void Main(string[] args)
  {
  	int a = 3;
	int b = 4;
  }
}

//想要在控制台中输出以下内容：
a = 3

//可以使用字符串连接符： + ，可以将字符串和数据（变量）相连接形成一个更大的字符串，如下：

class OutputDemo
{
  public static void Main(string[] args)
  {
  	int a = 3;
	System.Console.WriteLine("a = " + a);
  }
}

//想要在控制台中输出以下内容：
a = 3, b = 4

class OutputDemo
{
  public static void Main(string[] args)
  {
  	int a = 3;
	int b = 4;
	System.Console.WriteLine("a = " + a + ", b = " + b);
  }
}
```
C# 中还可以使用占位符的形式对数据进行输出，比如上述例子中使用占位符输出同样的效果：

```C#
class OutputDemo
{
  public static void Main(string[] args)
  {
  	int a = 3;
	int b = 4;
	System.Console.WriteLine("a = {0}, b = {1}", a, b);
  }
}
```
我们可以在字符串后面依次加入需要输出的变量，然后再字符串中以{0}、{1}…的形式来表示该变量。注意序号是从0开始的，但是顺序可以改变，比如System.Console.WriteLine(“a = {1}, b = {0}”, a, b);

同时，占位符还有格式化输出的功能，比如输出时间格式、货币格式，可以参考《叩响C#之门》2.4章节拓展理解。

### string类型与int类型的转换

我们可以在控制台中使用特定的函数在键盘上输入一定的内容：System.Console.ReadLine();
默认在控制台上输入的内容全都是字符串类型，有时候我们需要把字符串类型转化成int类型去做数值型的运算。我们可以使用System.Convert.ToInt32()函数将字符串类型的数字转换成int类型

```C#
class Demo
{
  public static void Main(string[] args)
  {
	string str = System.Console.ReadLine(); //控制台输入内容，用字符串类型接收
	int d = System.Convert.ToInt32(str);
	//这个函数可以将字符串类型的参数转换为int类型，把str中的字符串内容转换为int类型并用int类型接收。
	int a = 3;
	int c = a + d; //将两个int类型数据进行运算
	System.Console.WriteLine(c);  //得出结果
  }
}
```

