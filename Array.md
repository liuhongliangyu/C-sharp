# 数组
## 一维数组
### 一维数组定义
数组的概念：数组是同一种类型数据的集合，也是一个容器。

数组的特点：

* 数组里面的数据必须是同一类型（同一种数据类型的集合）
* 数组里面的数据自带编号，编号从0开始，叫索引（角标）
定义数组的格式一：元素类型[] 数组名 = new 元素类型[元素个数或数组长度]
```C#
class ArrayDemo
{
  public static void Main(string[] args)
  {
    int[] arr = new int[3]; //int类型的数组，里面有3个位置
    arr[2] = 30;//通过索引值向数组中放入元素
    arr[1] = 20;
    arr[0] = 10; //数组中的格子不一定都赋值，如果没赋值，有默认值是0
    //arr[3] = 40; //索引越界异常。IndexOutOfRangeException
    System.Console.WriteLine(arr[0]);//通过索引值打印对应的数据，输出10
    System.Console.WriteLine(arr[1]);//输出20
    System.Console.WriteLine(arr[2]);//输出30
  }
}
```
定义数组的格式二(两种)：

元素类型[] 数组名 = new 元素类型[]{元素, 元素….}
```C#
class ArrayDemo
{
  public static void Main(string[] args)
  {
    int[] arr = new int[]{10, 20, 30};
    System.Console.WriteLine(arr[0]);
    System.Console.WriteLine(arr[1]);
    System.Console.WriteLine(arr[2]);
  }
}
```
元素类型[] 数组名 = {元素, 元素….}
```C#
class ArrayDemo
{
  public static void Main(string[] args)
  {
    int[] arr = {10, 20, 30};
    System.Console.WriteLine(arr[0]);
    System.Console.WriteLine(arr[1]);
    System.Console.WriteLine(arr[2]);
  }
}
```
### 一维数组的使用
我们可以使用for循环或者foreach遍历一个数组里面所有的数据。

数组中有Length属性可以获得当前数组中所有元素个数。
```C#
class ArrayDemo
{
  public static void Main(string[] args)
  {
    int[] arr = {10, 20, 30};
    for(int i = 0; i < arr.Length; i += 2) 
    {
      System.Console.WriteLine(arr[i]);
    }
  }
}
```
使用foreach循环
```C#
class ArrayDemo
{
  public static void Main(string[] args)
  {
    int[] arr = {10, 20, 30};
  
    foreach(int Ele in arr)
    {
      System.Console.WriteLine(Ele); //输出数组中每一个数据
    }
  }
}
```
### 二维数组的定义
我们可以把一维数组理解成一行数据，一行里面可以放很多。而二维数组我们可以理解成一个平面，类似于表格，也就是包含行和列，即维数。

二维数组的定义格式：
数据类型[,] 变量名 = {{元素1, 元素2…}, {元素1, 元素2…}, {元素1, 元素2…}…}
```C#
class ArrayDemo
{
  public static void Main(string[] args)
  {
    int[,] arr = {{3,0,8}, {50,26,78}, {12,30,61}}; //定义一个3行3列的二维数组
  
    foreach(int Ele in arr)
    {
      System.Console.WriteLine(Ele); //输出数组中每一个数据
    }
  }
}
```
当我们要取出二维数组中的一个数据时，可这样：
```C#
class ArrayDemo
{
  public static void Main(string[] args)
  {
    int[,] arr = {{3,0,8}, {50,26,78}, {12,30,61}}; //定义一个3行3列的二维数组
  
    System.Console.WriteLine(arr[0, 2]);//打印8
  }
}
```
其他格式：数据类型[,] 变量名 = new int[行数,列数]；
```C#
class ArrayDemo
{
  public static void Main(string[] args)
  {
    int[,] arr2 = new int[3, 4]; //定义一个3行4列的数组，但没有添加数据
    arr[0, 0] = 10; //添加数据
    System.Console.WriteLine(arr[0, 0]); //打印为10
  }
}
```
### 二维数组的使用
目前情况下，二维数组的使用情况并不多见，所以我们在这个阶段简单介绍一下二维数组的遍历。

二维数组需要使用循环嵌套进行遍历。如：
```C#
class ArrayDemo
{
  public static void Main(string[] args)
  {
    int[,] arr = {{3,0,8}, {50,26,78}, {12,30,61}};

    //使用for循环遍历
    for(int i = 0; i < 4; i++)
    {
      for(int j = 0; j < 3; j++)
      {
        Console.WriteLine(arr[i, j]);//输出数组中每个数据
      }
    }

    //使用foreach遍历
    foreach(int Ele in arr)
    {
      System.Console.WriteLine(Ele);//输出数组中每个数据
    }
  }
}
```
**注意，二维数组的索引也是从0开始**
### 一维数组求最值

在一维数组的所有数据中找到最值（最大或最小）并输出，两种方法。

第一种：可以假设初始化最大值为数组里面索引为0的数字，然后依次拿后面的数据进行对比。
```C#
class ArrayDemo
{
  public static void Main(string[] args)
  {
    MaxMin2(); //调用方法，得到最大的数据
  }

  public static void MaxMin2()
  {
    int[] arr = {-3, -15, -55, -6, -28, -78};

    int Max = arr[0];

    for(int i = 0; i < arr.Length; i++)
    {
      if(arr[i] > Max)
      {
        Max = arr[i];
      }
    }
    System.Console.WriteLine(Max);
  }
}
```
第二种：初始化最大的数的角标，然后依次用后面的数据进行比较，得到最大的数字的角标。
```C#
class ArrayDemo
{
  public static void Main(string[] args)
  {
    MaxMin2(); //调用方法，得到最大的数据
  }

  public static void MaxMin3()
  {
    int[] arr = {-3, -15, -55, -6, -28, -78};

    int MaxIndex = 0; //初始化最大索引值

    for(int i = 0; i < arr.Length; i++)
    {
      if(arr[i] > arr[MaxIndex])
      {
        MaxIndex = i;
      }
    }
    System.Console.WriteLine(arr[MaxIndex]);
  }
}
```
一维数组二分法查找

采用二分法查找时，数据需是有序不重复的。 基本思想：假设数据是按升序排序的，对于给定值 x，从序列的中间位置开始比较，如果当前位置值等于 x，则查找成功；若 x 小于当前位置值，则在数列的前半段中查找；若 x 大于当前位置值则在数列的后半段中继续查找，直到找到为止。

折半查找前提：数组必须是有序的
```C#
class ArrayDemo
{
  public static void Main(string[] args)
  {
    int index = HalfSerach(45);
    System.Console.WriteLine(index);
  }

  public static int HalfSearch(int key)
  {
    int[] arr = {13, 15, 19, 28, 33, 45, 78, 106};

    int mid, min, max;
    min = 0;
    max = arr.Length - 1;
    mid = (min + max) / 2;

    while(arr[mid] != key)
    {
      if(key > arr[mid])
      {
        min = mid + 1;
      }
      else if(key < arr[mid])
      {
        max = mid - 1;
      }

      if(min > max)
      {
        return -1;
      }

      mid = (min + max) / 2;
    }
    return mid;
  }
}
```
一维数组选择排序

将数组中的数据排序。基本思想：首先以一个元素为基准，从一个方向开始扫描，如从左到右。以A[0]为基准，接下来从A[0]….A[9]中找出最小的元素，将其与A[0]交换。然后将其基准位置右移一位，重复上面的动作，比如，以A[1]为基准，找出A[1]~A[9]中最小的，将其与A[1]交换。一直进行到将基准位置移到数组最后一个元素时排序结束。
```C#
class ArrayDemo
{
  public static void Main(string[] args)
  {
    SelectSort();
  }

  public static void SelectSort()
  {
    int[] arr = {35, 20, 12, 110, 4, 57};

    for(int x = 0; x < arr.Length - 1; x++) //注意为什么 -1
    {
      for(int y = x + 1; y < arr.Length; y++)//注意int y = 1 + x ,形成变化的量
      {
        if(arr[x] > arr[y])
        {
          int temp = arr[x];
          arr[x] = arr[y];
          arr[y] = temp;
        }
      }
    }

    foreach(int ele in arr)
    {
      System.Console.WriteLine(ele);
    }
  }
}
```
一维数组冒泡排序

基本思想：将相邻的两个数比较，将较小的数调到前头；有n个数就要进行n-1趟比较，第一次比较中要进行n-1次两两比较，在第j趟比较中，要进行n-j次两两比较。
```C#
class ArrayDemo
{
  public static void Main(string[] args)
  {
    BubbleSort();
  }

  public static void BubbleSort()
  {
    int[] arr = {35, 20, 12, 110, 4, 57};

    for(int x = 0; x < arr.Length - 1; x++) //为什么 -1
    {
      for(int y = 0; y < arr.Length - x - 1; y++)  //为什么 - 1 - x 
      {
        if(arr[y] > arr[y + 1])
        {
          int temp = arr[y + 1];
          arr[y + 1] = arr[y];
          arr[y] = temp;
        }
      }
    }

    foreach(int ele in arr)
    {
      System.Console.WriteLine(ele);
    }
  }
}
```






