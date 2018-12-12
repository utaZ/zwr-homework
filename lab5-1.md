# 字符游戏 贪吃蛇


#include<stdio.h>
#include<stdlib.h>
#include"snake1.h"     
void move();           //移动 
void outputmap();       //输出地图 
void gameover();       //游戏结束 
void score();          //吃食物得分 
void set();             //初始化地图 
void score();          //吃食物得分 
//主函数 
int main(){          
    set();
    outputmap();
    gameover();
    return 0;
}12345678910111213141516

snake1.h代码



#include<stdio.h>
#include<stdlib.h>
int headx,heady,max,dir,begin;    //蛇头的坐标，方向，长度  
char in;                        //读取字符 
int map[12][12] = {0};        //地图 
int i, j, foodx, foody;        //食物 
//对于地图，根据初始化来定义地图，如-1为边界，0为内部，max为蛇身，100为食物 
void outputmap(){
    for(i=0;i<=11;i++){
        for(j=0;j<=11;j++){
        if(map[i][j]==-1)
        printf("*"); 
        if(map[i][j]==0)
        printf(" ");
        if(map[i][j]!=0&&map[i][j]!=-1&&map[i][j]!=max&&map[i][j]!=100)
        printf("X");
        if(map[i][j]==max)
        printf("H");
        if(map[i][j]==100)
        printf("$");
    }
        printf("\n");
    }
    return;
}

//吃食物函数 当蛇头碰到食物，身长加一，游戏继续 
void score(){
    if(map[headx][heady]!=100){
        map[headx][heady]=max+1;
        for(i=1;i<11;i++){
            for(j=1;j<11;j++){
                if(!(map[i][j]==0||map[i][j]==-1)){
                    map[i][j]--;
                }
            }
        }
        map[foodx][foody]=100;
    }
    else{
        max++;
        map[headx][heady]=max;
    }
    system("cls");         //清屏输出 
    outputmap();
    return;
}
//移动函数，读取用户输入一个字符，S为向下一格，W为向上一格，A为向左一格，D为向右一格
//不断输入，用EOF来作为结束判断 
void move(){
    if(begin==0){
        dir='d';
        begin++;
    }
    if(scanf("%c",&in)!=EOF)
    dir=in;
    switch(dir){
        case 'd':
            heady++;
            break;
        case 'a':
            heady--;
            break;
        case 'w':
            headx--;
            break;
        case 's':
            headx++;
            break;
    }
    return;
}
//游戏结束，当蛇头碰到边界或自己身体，判断游戏结束，跳出循环输出GAME OVER 
void gameover(){
    while(1){
        move();
        if(map[headx][heady]!=0&&map[headx][heady]!=max&&map[headx][heady]!=100){
            printf("Game Over!!!\n");
            break;
        }
        else
        score();
    }
}

//初始化地图，将地图赋值化后输出，跟outputmap函数一起调用 
void set(){
    for (i=0;i<=11;i++) {          
        map[i][0]=-1;                
        map[i][11]=-1;               
        map[0][i]=-1;              
        map[11][i]=-1;             
    }                                   
    for (i=1;i<=5;i++) {         
        map[1][i]=i;                   
    }                                 
    max=5;                         
    headx=1;                      
    heady=5;                                       
    begin=0;                      
}
