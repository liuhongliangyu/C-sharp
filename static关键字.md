## static关键字介绍

static（静态的）是系统保留的关键字，同时也是修饰符，可以用来修饰类及类的成员（方法、变量、属性）。

成员包括：成员变量、方法、属性（作用：可以吧变量进行封装，可以把变量进行赋值、取值）、构造函数（作用：初始化对象）

## 被static修饰的成员具备以下特点：

1. static是修饰符，用于修饰成员
1. 随着类的加载而加载，所以优先于对象存在
1. 被所有该类的对象所共享，所以需要被共享的数据才会被static修饰
1. 可以直接被类名调用，类名.静态成员，不能通过对象直接调用
1. static修饰的成员是共享数据，对象中的是特有数据。共享数据只占一份内存

static修饰的成员特点

变量被static修饰后就成为了静态变量，意味着这个变量被所有这个类的对象所共享，任何一个对象对这个变量做出了修改，其他对象也会收到影响。

## 静态变量和成员变量的区别
1. 生命周期不同：成员变量随着对象的创建而存在，随着对象的回收而释放。静态变量随着类的加载而存在，随着类的消失而消失（周期长）
1. 调用方式不同：成员变量只能通过对象来调用；静态变量只能通过类名来调用（类名.静态变量）
1. 别名不同：成员变量--实例变量；静态变量--类变量
1. 存储区域不同：成员变量存储在堆里；静态变量存储在静态（共享）区里。

函数也可以被static修饰。

被static修饰的成员有切仅有一种调用方式：类名.静态成员

## 静态类的特点

静态类就是用static关键字去修饰类，静态类的特点如下：

1. 仅包含静态成员。
1. 无法实例化。
1. 是密封的。
1. 不能包含实例构造函数。
1. 防止在类的内部声明任何实例字段或方法。
定义静态的原因：
```C#
class StaticDemo
{
  static void Main(string[] args)	//arguments参数
  {
    Person p1 = new Person("旺财");//创建对象
    Person p2 = new Person("小强");//创建对象
	//创建多个对象，发现在name和country两个变量中，name是对象特有的内容，而country都是CN，这样每一个对象都会占用不必要的内存空间
	p1.Speak();
	p2.Speak();
  }
}

class Person
{
  public string name;	
  public static string country = "中国";//所有的对象都是中国人，所以只需要将这个数据共享，它会单独定义在内存的共享区，只占用一份空间
    
  public Person(string name)
  {
 	this.name = name;
  }
    
  public void Speak()//非静态可以访问静态的内容
  {
	System.Console.WriteLine(name + ".." + country);
  }
}

```
调用静态内容：
```C#
class StaticDemo
{
  static void Main(string[] args)	//arguments参数
  {
    System.Console.WriteLine(Person.country);//静态内容只能通过类名调用
    Person p1 = new Person("旺财");//创建对象
    p1.country;//不能使用对象调用静态内容
    Person.Speak();//静态方法只能通过类名调用
 }
}

class Person
{
  public string name;	
  public static string country = "中国";//所有的对象都是中国人，所以只需要将这个数据共享。
    
  public Person(string name)
  {
 	this.name = name;
  }
    
  public static void Speak()//静态内容只能访问静态的
  {
	System.Console.WriteLine(".." + country);
  }
}
```

## static注意事项
1. 静态方法中只能访问静态成员（弊端，局限性），非静态可以访问静态，也能访问非静态的
1. 静态方法中不能使用this、base关键字
1. 主函数是静态的

## 什么时候使用static关键字
1. 静态变量：当分析对象中所具备的成员的内容是相同的，这时这个内容就可以修饰成static。但是如果想改变这个值，需要注意，其他对象的该内容也会改变。只要数据在对象中不同，
那就是对象的特有数据，必须存储在对象中，如果是相同的数据并且对象不需要对这个数据进行修改只需使用，就需要把该数据修饰成static。
1. 静态函数：函数是否使用static修饰，就参考一点，就是这个函数的功能是否需要访问这个函数所在的类中的非静态变量。
简单说，从源码上看，该功能是否需要访问这个类的非静态变量，如果需要，这个函数就定义城非静态的；如果不需要，就定义成静态的。因为调用方便、效率，不需要创建对象，节省内存空间。




