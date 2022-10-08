---
title: 关于动态规划完全背包问题
date: 2022-03-26 10:34:00 +0800
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


## 动态规划

题目：hdu1028
递推与递归做法
```c
//代码片段
#include<bits/stdc++.h>
using namespace std;
const int maxn=1e4;
int dp[maxn][maxn];//递推表达式dp[n][m]的含义,将n的划分最大数分成不超过m的划分数
/*状态转移方程：
    dp[i][j]=dp[i][j-1]+dp[i-j][j];(i>j)分治思想，将n的划分最大数分成不超过m的划分数有两种情况：
    1，不包含最大数j划分个数为dp[i][j-1],
    2.包含最大数j,划分个数为dp[i-j][j](包含指一定包含，所以i要减去J，转化为求子问题dp[i-j[j])
    dp[i][j]=dp[i][j-1]+1（i==j)是上述情况的特殊情况，此时,dp[i-j][j]为零，则包含最大数j只有一种情况即全部划分为j，且只有一个
    3.dp[i][j]=dp[i][i](i<j),当i<j那么肯定只能划分为dp[i][i]
    4.dp[i][j]=1(i==1||j==1),容易理解，特殊情况
*/
void part(){
    for(int i=1;i<maxn;i++){
        for(int j=1;j<maxn;j++){
            if(i==1||j==1)dp[i][j]=1;
            else if(i<j)dp[i][j]=dp[i][i];
            else if(i>j)dp[i][j]=dp[i][j-1]+dp[i-j][j];
            else if(i==j)dp[i][j]=dp[i][j-1]+1;
        }
    }
}
int main(){
    int n;
    part();
    while(cin>>n){
        printf("%d\n",dp[n][n]);
    };
    return 0;
}
```
还有动态规划：
完全背包
```c
#include<bits/stdc++.h>
using namespace std;
const int maxn=1e3;
int dp[maxn];//动态规划完全背包，滚动数组求解
//dp[i]的含义：划分数字i的最多数目
//状态转移方程：dp[i]+=dp[i-j];
void solve(){
    dp[0]=1;//注意
    for(int i=1;i<maxn;i++){//枚举每种数字
        for(int j=i;j<maxn;j++){//每种数字的重量与他的价值相等
            dp[j]+=dp[j-i];//由于单位价值都一样，且这题求的是
        }
    };
}
int main(){
    int n;
    solve();
    while(cin>>n){
        printf("%d\n",dp[n]);
    };
    return 0;
}

```

![算法](/pictrue/Thank_you_drop_kick.jpg)

=======
