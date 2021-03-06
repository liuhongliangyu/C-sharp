## 面向对象的概念

C#是面向对象语言，也就具备面向对象的特征。首先，面向的意思我们可以理解为面对，或者操作；而对象则可以理解为实体，实实在在存在的个体。日常生活中我们能看得见摸得着的物体都可以叫做对象。所以，面向对象我们可以理解成直接操作对象，而这个对象具备了很多特有的功能。

面向对象区别于面向过程，是面向过程里程碑式的升级。

面向对象举例：

* 上饭店吃饭时，点菜要找服务员而不是厨师，因为服务员具备点菜功能。
* 饭店做菜时要找厨师而不是服务员，因为厨师具有做饭功能。
以上两个例子，服务员和厨师都是对象，但他们具备的功能不一样。我们想实现什么样的功能，就找符合对应功能的对象即可。而这些点菜做菜的功能不需要我们自己去完成，省时省力。

## 类和对象的关系

类和对象的关系可以理解成为汽车图纸和小汽车的关系。在日常生活中，小汽车是如何生产的呢？一定是要有实现画好的图纸，然后按照图纸去生产小汽车，我们可以把图纸理解成为是对小汽车的描述；而小汽车则是实实在在存在的物体，所以小汽车就是对象。

在代码中，类就是图纸，用来描述对象；而对象则是通过这个图纸（类）创建出来的实体。类会描述出这个对象所具备的各种特征和功能，当我们想使用这些功能时，就要通过这个类的对象去使用。就好比我们无法通过汽车图纸直接把汽车开走一样，我们操作的是对象，所以在使用功能前也要先要有对象。

## 声明类

我们可以在同一个文件中声明多个类，比如：
```C#
class Program
{
  static void Main(string[] args)
  {

  }
}

class Car
{
//事物的特征
  public int num = 4;
  public string color = "红色";
//事物的行为（功能）
  public void Run()
  {
    Console.WriteLine(color + "的小汽车跑起来，" + num + "个轮子");
  }
}
```
其中，Car类可以理解为图纸，里面详细描述了一辆小汽车的特征（num和color变量）和功能（Run方法）

## 声明对象

当拥有一个类的时候，我们就可以通过这个类来创建它的对象，比如：
```C#
class Program
{
  static void Main(string[] args)
  {
    Car car = new Car();//new Car()就是这个类的对象，car是给这个对象起的名字，要有类型为Car
    car.Run(); //想使用汽车的Run功能，必须通过对象。通过 对象.成员 调用对象里面的内容

    Console.ReadLine();
  }
}

class Car
{

  public int num = 4;
  public string color = "红色";

  public void Run()
  {
    Console.WriteLine(color + "的小汽车跑起来，" + num + "个轮子");
  }
}
```
注意：成员就是组成类的部分，目前包括变量（字段）、方法。向使用成员必须通过对象。

## 总结

本节课中我们学习了类和对象的关系以及如何创建对象。在C#(面向对象)语言中，创建对象是常见的动作，所以大家必须要掌握创建对象的格式，并使用其中的内容。在学习过程中大家还必须要指导类和对象的关系。
