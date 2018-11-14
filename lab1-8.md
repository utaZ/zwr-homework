# 自顶向下，逐步求精

即Top-down design,将问题分解为一组称为模块的子问题;创建问题和子问题的层次结构（模块）。

![](https://github.com/utaZ/zwr-homework/blob/gh-pages/images/untitled.png)

自顶向下的分析算法通过在最左推导中描述出各个步骤来分析记号串输入。将大型的数字电路设计分割成大小不一的小模块来实现特定的功能，最后通过由顶层模块调用子模块来实现整体功能，这就是Top-Down的设计思想。

逐步求精是指将现实问题经过几次抽象（细化）处理，最后到求解域中只是一些简单的算法描述和算法实现问题。即将系统功能按层次进行分解，每一层不断将功能细化，到最后一层都是功能单一、简单易实现的模块。求解过程可以划分为若干个阶段，在不同阶段采用不同的工具来描述问题。在每个阶段有不同的规则和标准，产生出不同阶段的文档资料。

# 洗衣机问题

![](https://github.com/utaZ/zwr-homework/blob/gh-pages/images/timg1.jpg)

set the water in >> soap the clothes >> wash the clothes >> dewatering the clothes >> stop the work 

注水 >> 浸泡 >> 洗涤和漂洗 >> 脱水 >> 停机

## 伪代码

注水： 
   turn on the water_in_switch 
   set the water volume 
   while(water_input is less than the water volume) 
    keep the water_in_switch open 
   while(water_input is more than the water volume or volume timeout) 
    stop input water  

浸泡 
   set the soaping time 
   for(set the left time is zero ;the left time is less than the setting time; increase the left time) 
    keep the clothes soaping 
   if(the left time is equal to the setting time) 
    begin to wash    

洗涤和漂洗 
   set the washing times to 3 
   set the washing time to 20 
   for(set a to zero; a is less than setting times; add 1 to a;) 
        if(the washing times is not the 1st time) 
         pouring the water 
         pouring in the new and clean water 
       do 
       washing and motor runs 
       while(the pass time is less than the washing time) 
       pouring the water  

脱水 
   set the motor run’s frequency 
   set the running  time 
   while the past time is less than the running time 
           keep the motor running in the setting frequency
