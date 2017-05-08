## static关键字介绍

static（静态的）是系统保留的关键字，同时也是修饰符，可以用来修饰类及类的成员。

## 被static修饰的成员具备以下特点：

* 随着类的加载而加载
* 优先与对象存在
* 被所有该类的对象所共享
* 可以直接被类名调用
## static修饰的成员特点

变量被static修饰后就成为了静态变量，意味着这个变量被所有这个类的对象所共享，任何一个对象对这个变量做出了修改，其他对象也会收到影响。

函数也可以被static修饰。

被static修饰的成员有切仅有一种调用方式：类名.静态成员

## 静态类的特点

静态类就是用static关键字去修饰类，静态类的特点如下：

* 仅包含静态成员。
* 无法实例化。
* 是密封的。
* 不能包含实例构造函数。
* 防止在类的内部声明任何实例字段或方法。
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
## 什么时候使用静态？

当数据需要共享时可以将变量修饰为静态，所有对象共享一个变量；

当方法不需要访问非静态的内容是可以修饰为静态，因为直接通过类名访问很快，不需要创建对象。

## 总结

本节课中我们讲解了static关键字，static 修饰的字段用于共享，修饰的方法可以直接被类名调用。大家要明确什么时候使用static，正确的使用static。
