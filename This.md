## this关键字的作用

this代表对象，当前对象。

专业术语：this就是代表所在函数所属对象的引用

简单说：哪个对象调用了this所在的函数，this就代表哪个对象

一般用于区分成员变量和局部变量重名

## this关键字的应用

* 什么时候使用this关键字？

**当函数内需要用到调用函数的对象时就用this。**
```C#
class ThisDemo
{
  static void Main(string[] args)
  {
    //Person p = new Person(10);
    //p.Run(10);
				
    Person p1 = new Person(20, "旺财");
    Person p2 = new Person(20, "小强");
				
    bool bo = p1.Compare(p2);//直接传入Person，更符合面向对象思想
   //bool bo = p1.Compare2(p2.age);可以直接传入年龄
    System.Console.WriteLine(bo);
    }
}

class Person
{
  public int age;
  public string name;
		
  public Person()
  {
      System.Console.WriteLine("A");
  }
		
  public Person(int age)
  {
    this.age = age;//使用 this关键字对重名成员变量和局部变量区分
    //System.Console.WriteLine(age);
  }
		
  public Person(int age, string name)
  {
    this.age = age;
    this.name = name;
    System.Console.WriteLine(name + ".." + age);
  }
		
  public void Run(int age)
  {
     //int age = 10;
    this.age = age;//使用this关键字对成员变量和局部变量重名下的区分
				
    System.Console.WriteLine(this.age);
  }
		
  public bool Compare(Person p)//使用this代表当前对象
  {
    return this.age == p.age;//是人的年龄和人的年龄做比较
  }
		
  public bool Compare2(int age)
  {
    return this.age == age;
  }
}
```
this还可以用来区分成员变量和局部变量重名的情况

## 总结

本节课中我们讲解了this关键字的用法，this可以代表其所在函数所属的对象，大家应该掌握使用this关键字的场景。
