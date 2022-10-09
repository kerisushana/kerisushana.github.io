---
title: 初学生成函数
date: 2022-10-9 10:34:00 +0800
categories: [算法]
tags: [学习]
pin: true
author: kerisuchiaki
author: minamichiaki
toc: true
comments: true
typora-root-url: ../../kerisuchiaki.github.io
math: true
mermaid: true
image:
  src: /C:\Users\minamichiaki\Pictures
  alt: 发布成功

---
生成函数也即是母函数

---
还挺妙的啊
```c
#include<bits/stdc++.h>
using namespace std;
const int maxn=1e3;
int s1[maxn],s2[maxn];//s1数组是保存结果的数组，s2是保存临时结果数组，另一种看法s[i]保存的结果为级数每一项的幂次为i的系数
void cal(){
    for(int i=0;i<maxn;i++)s1[i]=1,s2[i]=0;//一开始s1数组保存第一个级数的结果,也就是
    //即1+x+x^2+x^3+x^4....
    for(int k=2;k<maxn;k++){//开始计算数字包含2的级数，然后逐渐计算数字包含3，4，5的级数
    for(int i=0;i<maxn;i++){
        for(int j=0;j<maxn;j+=k){//遍历级数
            s2[i+j]+=s1[i];//计算结果
        }
    };
    for(int i=0;i<maxn;i++){
        s1[i]=s2[i];s2[i]=0;
    }
}
}
int main(){
    int n;
    cal();
    while(cin>>n){
        printf("%d\n",s1[n]);
    };
    return 0;
}
```
也许这张图解释地更好
![算法](/pictrue/2022-10-9-learn_node.png)
