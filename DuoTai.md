## 多态的概念

多态是面向对象三大特征之一，是基于继承之上的一种表现形式，是面向对象重要的特性。多态就是同一种事物在不同的情况下表现不同的对应的形态。

## 多态的表现形式

我们通过代码来演示多态，首先先看一下之前写的代码：
```C#
  class Animal
  {
    public void Eat()
    {
      Console.WriteLine("吃饭");
    }
  }

  class Cat : Animal    //Cat类继承Animal类
  {
  }

  class Demo
  {
    static void Main(string[] args)
    {
      Cat cat = new Cat();    //以往我们创建对象的时候要“左右类型一致”
      cat.Eat();    //通过cat调用从Animal类继承下来的Eat方法，输出为吃饭

      Animal a = new Animal();
      a.Eat();   //我们还可以创建Animal类的对象并调用它自身的Eat方法，结果也是吃饭
    }
  }
```
其实我们要更详细的分析这个问题。我们发现，实际上Animal包含很多种类，不仅仅是Cat。而大体上每一种类的“吃”的行为的内容都不一样，比如猫要吃鱼，狗要吃骨头等等。所以，我们应该考虑到所有的动物都有吃的行为，而吃的内容不一样，这时候我们可以把Animal定义成抽象类。
```C#
  abstract Animal   //抽象类Animal
  {
    abstract public void Eat();   //意味着所有的动物都有吃的功能
  }

  class Cat : Animal
  {
    public override void Eat()    //猫类（子类）重写父类方法为自己的表现形式“猫吃鱼”
    {
      Console.WriteLine("猫吃鱼");
    }
  }

  class Dog : Animal
  {
    public override void Eat()    //狗类（子类）重写父类方法为特有表现形式“狗啃骨头”
    {
      Console.WriteLine("狗啃骨头");
    }
  }

  class Demo
  {
    static void Main(string[] args)
    {
      Animal a1 = new Cat();    //多态，动物当做猫
      a1.Eat();   //结果是“猫吃鱼”

      Animal a2 = new Dog();    //多态，动物又当做狗
      a2.Eat();   //结果是“狗啃骨头”
    }
  }
```
根据以上代码我们可以发现，“动物”本身是一个抽象的概念，但是它有具体的子类实现。当“动物”被当做不同的具体子类时，会产生不同的效果，即当做小猫就会吃鱼，当做小狗就会啃骨头。这就是多态的具体表现形式，同一个事物在不同的情况下表现出不同的对应形态。

向上转型

多态实际上就是类型转换。
```C#
class DuoTaiDemo
{
  public static void Main(string[] args)
  {
    Animal animal = new Cat();//向上转型
    Cat c = new Cat();
	Method(c);
  }
  //定义一个方法，可以指挥任何动物吃东西
  public static void Method(Animal animal)//传进来的动物可以被看做Animal，也是向上转型
  {
    animal.Eat();//传进来什么对象就会调用该对象的功能
  }
}

abstract class Animal
{
  public abstract void Eat();//定义小动物的吃饭功能
}

class Cat : Animal
{
  public override void Eat()
  {
    System.Console.WriteLine("猫吃鱼");
  }
	
  public void CatchMouse()
  {
    System.Console.WriteLine("抓老鼠");
  }
}

class Dog : Animal
{
  public override void Eat()
  {
    System.Console.WriteLine("吃骨头");
  }
	
  public void LookHome()
  {
    System.Console.WriteLine("狗看家");	
  }
}

这句代码中，Cat是Animal的子类，实际上是子类型自动提升到父类型，这是之前学习的自动类型提升，也就是向上转型。
```
向下转型

多态中还可以有向下转型，即把父类型转换为子类型，比如：
```C#
class DuoTaiDemo
{
  public static void Main(string[] args)
  {
    Animal a = new Cat();   //向上转型
    Cat c = (Cat)a;   //向下转型
  }
}
12345678
第二句代码就是向下转型。但是要注意，只有被向上转型过的才能被向下转型，也就是说如果没有第一句代码则不成立。好比下面：（抛去抽象类不能创建对象的问题）

class DuoTaiDemo
{
  public static void Main(string[] args)
  {
    Animal a = new Animal();
    Cat c = (Cat)a;
  }
}

这样写就一定是错误的，因为在向下转型前没有向上转型。
```
多态中的重写（覆盖）

重写是很重要的概念，之前我们已经学过。在多态中，重载还有一些小细节需要掌握：
 ```C#
  class Fu
  {
    public virtual void Show()
    {
      Console.WriteLine("Fu");
    }
  }

  class Zi : Fu   //继承
  {
    public override void Show()   //重写父类方法
    {
      Console.WriteLine("Zi");
    }
  }

  class Demo
  {
    static void Main(string[] args)
    {
      Zi zi = new Zi();   //子类对象，子类类型
      zi.Show();    //结果是Zi

      Fu fu = new Zi();   //子类对象，父类类型
      fu.Show();    //结果是Zi
    }
  }

  根据以上得出结论：在多态中，重写会调用子类的方法。
```
## 多态的好处

我们发现，多态的出现使我们的代码的设计更加灵活：

当不断的有新的小动物添加时，我们只需要新写一个类并继承Animal，重新实现已经写好的父类抽象方法即可，不必重新定义新功能，提高了代码的复用性。

程序后期会不断添加新的类及功能，但是我们发现只要这新类都继承自Animal，那么无论是后期来的任何对象的Eat方法都可以被Animal调用，即后期的内容可以被前期的代码所调用，提高了程序的可维护性。

## 子类对父类中虚方法的处理有重写（override）和覆盖（new），请说明它们的区别？
有父类ParentClass和子类ChildClass、以及父类的虚方法VirtualMethod。有如下程序段：

ParentClass pc = new ChildClass();pc.VirtualMethod(…);

如果子类是重写（override）父类的VirtualMethod，则上面的第二行语句将调用子类的该方法

如果子类是覆盖（new）父类的VirtualMethod，则上面的第二行语句将调用父类的该方法

## Override与重载有什么区别？
重载是提供了一种机制, 相同函数名通过不同的返回值类型以及参数来表来区分的机制

override是用于重写基类的虚方法,这样在派生类中提供一个新的方法

覆写（Override）的两个函数的函数特征相同，重载（Overload）的两个函数的函数名虽然相同，但函数特征不同。函数特征包括函数名，参数的类型和个数。
### override
使用 override 修饰符来修改方法、属性、索引器或事件。重写方法提供从基类继承的成员的新实现。由重写声明重写的方法称为重写基方法。重写基方法必须与重写方法具有相同的签名。
不能重写非虚方法或静态方法。重写基方法必须是虚拟的、抽象的或重写的。
也就是说，用 override 修饰符重写的基类中的方法必须是 virtual, abstract 或 override 方法
### 重载
当类包含两个名称相同但签名不同的方法时发生方法重载。

使用重载方法的指南:
1. 用方法重载来提供在语义上完成相同功能的不同方法。
1. 使用方法重载而不是允许默认参数。默认参数的版本控制性能不好，因此公共语言规范(CLS)中不允许使用默认参数。
1. 正确使用默认值。在一个重载方法系列中，复杂方法应当使用参数名来指示从简单方法中假定的默认状态发生的更改。
1. 对方法参数使用一致的排序和命名模式。提供一组重载方法，这组重载方法带有递增数目的参数，以使开发人员可以指定想要的级别的信息，这种情况很常见。您指定的参数越多，开发人员就可指定得越详细。
1. 如果必须提供重写方法的能力，请仅使最完整的重载是虚拟的并根据它来定义其他操作。
```C#
abstract class BaseClass
{
  public virtual void MethodA()
  {
  }

  public virtual void MethodB()
  {
  }
}

class Class1: BaseClass
{
  public void MethodA(string arg)
  {
  }

  public override void MethodB()
  {
  }
}

class Class2: Class1
{
  new public void MethodB()
  {
  }
}

class MainClass
{
  public static void Main(string[] args)
  {   
    Class2 o = new Class2();
    Console.WriteLine(o.MethodA());
  }
}
```
请问，o.MethodA调用的是()
