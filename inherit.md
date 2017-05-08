## 继承的概念

继承是面向对象三大特征之一，是面向对象语言一项重要的机制。借助继承，可以扩展原有的代码，应用到其他程序中，而不必重新编写这些代码。具体的可以表述为： 继承可以使得子类具有父类的内部的大部分内容，而不需要再次编写相同的代码。

多个类中存在相同特征或行为时，可以将这些相同的内容抽取到单独一个类中，那么多个类无需再定义这些特征和行为，只要继承单独的那个类即可。多个类可以称为子类，单独这个类称为父类或者超类。子类可以直接访问父类中的非私有的字段和方法。

继承的表现形式
```C#
class ExtendDemo
{
  public static void Main(string[] args)
  {
    Student s = new Student();
    s.name = "旺财";
    s.age = 20;
    s.Speak();
    s.Study();
		
    Worker w = new Worker();
    w.name = "旺财";
    w.age = 20;
    w.Speak();
    w.Work();
  }
}

//定义一个Person类，将Sutdent和Worker的共同内容进行抽离形成一个新的类
class Person
{
  public string name;
  public int age;	
  
  public void Speak()//定义说话功能
  {
    System.Console.WriteLine("说话");	
  }
}

//学生类
class Student : Person  //形成继承关系，Student继承了Person
{
  /*Student和Worker类中的共性内容不必要再定义了，只需要继承Person即可
  public string name;
  public int age;*/
	
  public void Study()//定义特有学习功能
  {
    System.Console.WriteLine("学习");	
  }	
	
  /*
  public void Speak()//定义说话功能
  {
    System.Console.WriteLine("说话");	
  }*/
}

//工人类
class Worker : Person
{
  /*
  public string name;
  public int age;*/
  
  public void Work()//定义特有工作功能
  {
    System.Console.WriteLine("工作");	
  }	
	/*
  public void Speak()//定义说话功能
  {
    System.Console.WriteLine("说话");	
  }*/
}
```
根据上述例子我们发现，如果实现了继承关系，即使子类中没有定义Person类中的内容，子类对象也可以调用Person类中的内容。这就是继承关系。如果后续还有其他类写进来，只需要继承Person而不需要去重新定义这些重复的内容，提高了代码的扩展性和复用性。

## 继承的特点和好处

* 继承的出现提高了代码的复用性。
* 继承的出现提高了工作效率。
* 继承的出现提高了代码的扩展性
* 继承的出现让类与类之间产生了关系，提供了多态的前提。
* C#中类与类之间只支持单继承，不支持多继承（一个子类只能有一个直接父类）

C# 不支持多继承的原因：
```C#
class ExtendDemo
{
  public static void Main(string[] args)
  {
    new C().Show();//创建C对象，这时候调用Show会产生不确定性。所以C#不支持多继承
  }
}

class A
{
  public void Show()//定义Show方法
  {
    Console.WriteLine("A");
  }
}

class B
{
  public void Show()//同样的Show方法，但内容不一样
  {
    Console.WriteLine("B");
  }
}

class C : A, B //C类同时继承A和B类
{
}
```
继承中，子类可以继承父类的内容包括：字段、属性、普通函数。而构造函数、析构函数无法被继承

继承的细节

继承中有可能出现以下特殊情况：

* 子父类中有重名变量
```C#
    //定义一个父类
    class Fu
    {
      public int a = 3;
    }

    //定义一个子类继承父类
    class Zi : Fu
    {
      public new int a = 4;   //如果子父类中有重名的变量，一般要使用关键字new将父类的隐藏来消除警告。
      public void Z()
      {
        Console.WriteLine(a);
      }
    }

    //Main函数
    Main()
    {
      new Zi().Z();  //调用子类的“Z()”方法会打印出4
    }
```
* 子父类中有相同的方法声明而执行内容不一样

如果子父类中有相同的方法声明而执行内容不一样，我们也可以在子类的方法中使用new关键字对父类的方法进行隐藏。但一般不这么做，而是在父类的方法中用关键字virtual来修饰表示这是一个虚方法，可以被子类重写（覆盖）。子类的方法则用override来修饰表示是重写的父类方法。
```C#
  //定义一个父类，里面有Show方法为打印"Fu"
  class Fu
  {
    public virtual void Show()  //用virtual关键字修饰需要被子类重新实现的方法，也可叫虚方法
    {
      Console.WriteLine("Fu");
    }
  }

  //定义一个子类继承父类，子类有自己的Show方法为打印"Zi"
  class Zi : Fu
  {
    public override void Show()   //重新实现父类的Show方法
    {
      Console.WriteLine("Zi");
    }
  }

  //Main函数
  Main()
  {
    new Zi().Show();  //调用“Show()”方法会打印出子类的方法"Zi"
  }
```
## sealed关键字

sealed 是C#语法保留的关键字，同时也是修饰符，表示密封的。可以应用于类、方法和属性。被sealed修饰的类不能被继承。被sealed修饰的方法会重写基类中的方法，但其本身不能在任何派生类中进一步重写。当应用于方法或属性时，sealed 修饰符必须始终与 override 一起使用。

## protected权限修饰符

protected权限修饰符主要应用在子父类的继承关系中。子类可以继承父类中所有的字段、属性及方法，但是如果这些内容的权限是private，子类是无法使用继承下来的这些内容的。所以被protected修饰的内容只可以被自身及其子类来访问，其他的类无法访问。我们可以这么说：protected的权限要比private大一些。
```C#
class ExtendDemo
{
  public static void Main(string[] args)
  {
    new B().Show();//打印3
  }
}

class A
{
  protected int a = 3;//将a修饰成protected，意味着只有A和其子类才能访问这个变量
  //如果修饰成private则只有本类才可访问，子类也不能访问
}

class B : A
{
  public void Show()
  {
    Console.WriteLine(a);//打印继承下来的a变量
  }
}
```

## sealed修饰的类有什么特点？
密封，不能继承sealed 修饰词可套用至类别 (Class)、执行个体方法 (Instance Method) 和属性。密封类别无法被继承。密封方法会覆写基底类别 (Base Class ) 中的方法，但在任何衍生类别中却无法进一步覆写密封方法本身。当套用至方法或属性时，sealed 修饰词必须一律和 override (C# 参考) 搭配使用。

## 请解释virtual的含义？
virtual 关键字用于修改方法或属性的声明，在这种情况下，方法或属性被称作虚拟成员。虚拟成员的实现可由派生类中的重写成员更改。调用虚方法时，将为重写成员检查该对象的运行时类型。将调用大部分派生类中的该重写成员，如果没有派生类重写该成员，则它可能是原始成员。默认情况下，方法是非虚拟的。不能重写非虚方法。不能将 virtual 修饰符与以下修饰符一起使用：static abstract override除了声明和调用语法不同外，虚拟属性的行为与抽象方法一样。在静态属性上使用 virtual 修饰符是错误的。通过包括使用 override 修饰符的属性声明，可在派生类中重写虚拟继承属性
