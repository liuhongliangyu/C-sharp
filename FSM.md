## 有限状态机的介绍

有限状态机，（英语：Finite-state machine, FSM），又称有限状态自动机，简称状态机，是表示有限个状态以及在这些状态之间的转移和动作等行为的数学模型。

状态存储了关于过去的信息，就是说，它反映从系统开始到现在时刻的输入变化。转移指示状态变更，并且用必须满足来确使转移发生的条件来描述它。动作是在给定时刻要进行的活动的描述。

## 示例

2状态
编写程序，可以在控制台中读入字符串，字符串中有连续的空格。可以把连续的空格缩减为1个，剩下的原样输出。
```C#
class FSMDemo
{
  public static void Main(string[] args)
  {
    string str = System.Console.ReadLine();
    
    int sta = 0; //定义初始状态为0状态

    for(int i = 0; i < str.Length; i++) //循环遍历字符串
    {
      switch(sta)
      {
        case 0:
          if(str[i] == ' ')
          {
            sta = 1;
            System.Console.Write(' ');
          }
          else
          {
            sta = 0; //这句话可以不写，但为了表示状态的变化最好要写
            System.Console.Write(str[i]);
          }
          break;
        case 1:
          if(str[i] == ' ')
          {
            sta = 1; //如果维持在状态1，则不能输出内容
          }
          else
          {
            sta = 0;
            System.Console.Write(str[i]);
          }
          break;
        default:
          System.Console.Write("wrong state");
          break;
      }
    }
  }
}
```
