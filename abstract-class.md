## 抽象类的概念

抽象类是基于继承的表现形式，可以理解为特殊的类。

抽象定义：抽象就是从多个事物中将共性的，本质的内容抽取出来。例如：狼和狗共性都是犬科，犬科就是抽象出来的概念。

抽象类定义：C#中可以定义没有方法体的方法，该方法的具体实现由子类完成，这种方法称为抽象方法，包含抽象方法的类就是抽象类。

抽象方法的由来：不同的对象可能具备相同的功能，但是功能具体内容有所不同，那么在抽取过程中，只抽取了功能的定义，并未抽取功能主体，那么只有功能的声明，这种没有功能主体的方法称为抽象方法。

抽象类中的抽象方法必须要由其子类重新实现才可以使用。

继承的表现形式

抽象类和抽象方法都需要用abstract关键字来修饰：
```C#
abstract class Animal
{
  public int a = 3;
  public abstract void Eat();
}

class Dog : Animal  //子类继承抽象类
{
  public override void Eat()  //重新实现Eat方法
  {
    Console.WriteLine("啃骨头" + a);
  }
}

class Demo
{
  static viod Main(string[] args)
  {
    new Dog().Eat();  //只有实例化子类才可以调用方法
  }
}

```
## 抽象类的特点

* 抽象类和抽象方法必须用abstract关键字来修饰。
* 抽象方法只有方法声明，没有方法体，定义在抽象类中。格式：修饰符abstract 返回值类型函数名(参数列表)。
* 抽象类不可以被实例化，也就是不可以用new创建对象。因为抽象类是具体事物抽取出来的，本身是不具体的，没有对应的实例。例如：犬科是一个抽象的概念，真正存在的是狼和狗。
* 抽象类通过其子类实例化，而子类需要覆盖（重写）抽象类中所有的抽象方法后才可以创建对象，否则该子类也是抽象类。
* 抽象类里面可以有非抽象方法。
## 抽象类与普通类的区别

* 抽象类声明时要使用abstract关键字来定义，而普通类不需要。
* 抽象类里的抽象方法不能有方法主体, 只能有方法的声明。
* 抽象类被继承时、子类必须重新实现它的所有抽象方法，而普通类不需要。
* 抽象类里面大多数情况下要有抽象方法，而普通类里面一定没有抽象方法。

## 虚方法（virtual ）和抽象方法（abstract）的区别？
1. 抽象方法仅有声明，而没有任何实现，如abstract someMethod();，虚方法却不能如此
virtual用于修饰方法、属性、索引器或事件声明，并使它们可以在派生类中被重写。
2. 子类继承父类，可以对父类中的虚方法进行重写、覆盖、不处理三种处理，对抽象方法却必须实现

写出程序的输出结果
```C#
public abstract class A
{
  public A()
  {
    Console.WriteLine('A');
  }

  public virtual void Fun()
  {
    Console.WriteLine("A.Fun()");
  }
}

public class B: A
{
  public B()
  {
    Console.WriteLine('B');
  }

  public new void Fun()
  {
    Console.WriteLine("B.Fun()");
  }

  public static void Main()
  {
    A a = new B();
    a.Fun();
  }
}
```
