# 硬件编程–机器指令编程
18342146 邹文睿

![](https://github.com/utaZ/zwr-homework/blob/gh-pages/images/0.jpg)

## 任务 1：简单程序

### （1）打开网页 The PIPPIN User’s Guide ，然后输入 Program 1：Add 2 number
![](https://github.com/utaZ/zwr-homework/blob/gh-pages/images/1.jpg)

### （2）点step after step。观察并回答下面问题：
#### PC，IR 寄存器的作用
PC(program counter):程序计数器，用来计数，指示指令在存储器的存放位置，也就是地址信息

IR(instruction register):指令寄存器，用来存放指令，存放当前正在执行的指令，包括指令的操作码，地址码，地址信息
#### ACC 寄存器的全称与作用
accumulator累加器，是一种寄存器，用来储存计算产生的中间结果，即操作数或运算结果等
#### 用“LOD #3”指令的执行过程，解释Fetch-Execute周期
--->PC-->RAM-->IR-->Decoder-->MUX-->ALU-->PC

                 -->MUX------------>
                 
在第一个地址读取RAM的指令，将指令传输到IR中，操作码“LOD”被传输到decoder中解码，作为“=”传输到MUX，再传输到ALU中；操作数“3”被直接传到MUX，ALU中，ALU执行运算“=3”，并储存在ACC中，再返回PC
#### 用“ADD W” 指令的执行过程，解释Fetch-Execute周期
RAM-->DECODER-->MUX-->ALU-->ACC-->ALU-->ACC

   -->MUX-->RAM-->MUX------------>
   
指令传输到IR，“ADD”传输到DECODER，MUX，在ALU中“+”，再到ACC中取出“7”，输入到ALU中；“W”被传到MUX中，到RAM取出W的值3，返回MUX，输入ALU中，经运算将结果10输入到ACC中
#### “LOD #3” 与 “ADD W” 指令的执行在Fetch-Execute周期级别，有什么不同
后者更加复杂，需要到acc和ram中取出之前计算的值再进行计算，而前者不用
### （3）点击“Binary”,观察回答下面问题

#### 写出指令 “LOD #7” 的二进制形式，按指令结构，解释每部分的含义
00010100 00000111

操作符    操作数
#### 解释 RAM 的地址
每个操作占用2位的地址

地址表示为8位二进制数
#### 该机器CPU是几位的？（按累加器的位数）
8位
#### 写出该程序对应的 C语言表达
c语言：#include<stdio.h>

      int main(){
      
      int w=3;
      
      int x=7;
      
      int y;
      
      y=w+x;}
## 任务 2：简单循环
###（1） 输入程序Program 2，运行并回答问题：
![]()
#### 用一句话总结程序的功能
将x=3每次减1减至0
#### 写出对应的 c 语言程序
c语言：#include<stdio.h>

      int main(){
      
       int x=3;
       
       do{x=x-1;}
       
       while(x>0);}
### （2） 修改该程序，用机器语言实现 10+9+8+..1 ，输出结果存放于内存 Y
#### 写出 c 语言的计算过程
c语言：#include<stdio.h>

      int main(){
      
      int x=10;
      
      int y=0;
      
      do{y=y+x;
      
         x=x-1;}
         
      while(x!=0);}
#### 写出机器语言的计算过程
#### 用自己的语言，简单总结高级语言与机器语言的区别与联系
联系：都可用于编程；

区别：高级语言易于程序员理解使用，而机器语言可由电脑CPU解读使用
