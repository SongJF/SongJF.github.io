---
title: ACM小组第一次培训作业
author: SongJF
date: 2018-11-03 13:41:54
categories: ACM小组培训
tags:
---

<!-- TOC -->

- [1001](#1001)
- [1002](#1002)
- [1003](#1003)
- [1004](#1004)
- [1005](#1005)
- [1006](#1006)
- [1007](#1007)

<!-- /TOC -->

<!--more-->

## 1001

>Problem Description
>>Your task is to Calculate a + b.
Too easy?! Of course! I specially designed the problem for acm beginners. 
You must have found that some problems have the same titles with this one, yes, all these problems were designed for the same aim. 
>
>Input
>>The input will consist of a series of pairs of integers a and b, separated by a space, one pair of integers per line. 
>
>Output
>>For each pair of input integers a and b you should output the sum of a and b in one line, and with one line of output for each line in input.
>
>Sample Input
>>1 5</br>
10 20
>
>Sample Output
>>6 </br>
30


``` c
#include<stdio.h>
int main()
{
    int a,b;
    while(scanf("%d%d",&a,&b)!=EOF)
    {
        a+=b;
        printf("%d\n",a);
    }
    return 0;
}
```

## 1002

>Problem Description
>>Your task is to Calculate a + b.
>
>Input
>>Input contains an integer N in the first line, and then N lines follow. Each line consists of a pair of integers a and b, separated by a space, one pair of integers per line.
>
>Output
>>For each pair of input integers a and b you should output the sum of a and b in one line, and with one line of output for each line in input.
>
>Sample Input
>>2</br>
1 5</br>
10 20
>
>Sample Output
>>6 </br>
30

``` c
#include<stdio.h>
int main()
{
    int a,b,n;
    scanf("%d",&n);
    while(n--)
    {
        scanf("%d%d",&a,&b);
        a+=b;
        printf("%d\n",a);
    }
    return 0;
}
```

## 1003

>Problem Description
>>Your task is to Calculate a + b.
>
>Input
>>Input contains multiple test cases. Each test case contains a pair of integers a and b, one pair of integers per line. A test case containing 0 0 terminates the input and this test case is not to be processed.
>
>Output
>>For each pair of input integers a and b you should output the sum of a and b in one line, and with one line of output for each line in input.
>
>Sample Input
>>1 5</br>
10 20</br>
0 0
>
>Sample Output
>>6 </br>
30

``` c
#include<stdio.h>
int main()
{
    int a,b;
    while(scanf("%d%d",&a,&b)!=EOF)
    {
        if(a==0&&b==0) break;
        a+=b;
        printf("%d\n",a);
    }
    return 0;
}
```

## 1004

>Problem Description
>>Your task is to Calculate a + b.
>
>Input
>>Input contains an integer N in the first line, and then N lines follow. Each line starts with a integer M, and then M integers follow in the same line.
>
>Output
>>For each group of input integers you should output their sum in one line, and you must note that there is a blank line between outputs.
>
>Sample Input
>>3</br>
4 1 2 3 4</br>
5 1 2 3 4 5</br>
3 1 2 3
>
>Sample Output
>>10</br></br>
15</br></br>
6

``` c
#include<stdio.h>
int main()
{
    int n;
    scanf("%d",&n);
    while(n--)
    {
        int m,a,sum=0;
        scanf("%d",&m);
        for(int i=1;i<=m;i++)
        {
            scanf("%d",&a);
            sum+=a;
        }
        printf("%d\n",sum);
        if(n!=0) printf("\n");
    }
    return 0;
}
```

## 1005

>Problem Description
>>输入一个字符串，判断其是否是C的合法标识符
>
>Input
>>输入数据包含多个测试实例，数据的第一行是一个整数n,表示测试实例的个数，然后是n行输入数据，每行是一个长度不超过50的字符串。
>
>Output
>>对于每组输入数据，输出一行。如果输入数据是C的合法标识符，则输出"yes"，否则，输出“no”。
>
>Sample Input
>>3</br>
12ajf</br>
fi8x_a</br>
ff  ai_2
>
>Sample Output
>>no</br>
yes</br>
no</br>

``` c
#include<stdio.h>
#include<string.h>
using namespace std;
int main()
{
    int n;
    scanf("%d",&n);
    getchar();
    while(n--)
    {
        int len,flag=0;
        char a[100]; 
        gets(a);
        len=strlen(a);
        if(a[0]>='a'&&a[0]<='z') ;
        else if(a[0]>='A'&&a[0]<='Z') ;
        else if(a[0]=='_') ;
        else 
        {
            flag=1;
        }
        for(int i=1;i<len;i++)
        {
            if(flag==1) break;
            if(a[i]>='a'&&a[i]<='z') ;
            else if(a[i]>='A'&&a[i]<='Z') ;
            else if(a[i]=='_') ;
            else if(a[i]>='0'&&a[i]<='9') ;
            else
            {
                flag=1;
            }
        }
        if(flag==0) printf("yes\n");
        else printf("no\n");                                                                          
    }
    return 0;
}
```

## 1006

>Problem Description
>>有一个长度为n(n<=100)的数列，该数列定义为从2开始的递增有序偶数，现在要求你按照顺序每m个数求出一个平均值，如果最后不足m个，则以实际数量求平均值。编程输出该平均值序列。
>
>Input
>>输入数据有多组，每组占一行，包含两个正整数n和m，n和m的含义如上所述。
>
>Output
>>对于每组输入数据，输出一个平均值序列，每组输出占一行。
>
>Sample Input
>>3 2</br>
4 2
>
>Sample Output
>>3 6 </br>
3 7</br>

``` c
#include<stdio.h>
int main()
{
    int n,sum,m,x,flag,cnt;
    while(scanf("%d%d",&n,&m)!=EOF)
    {
        x=0;
        sum=0;
        flag=0;
        cnt=0;
        for(int i=1;i<=n;i++)
        {
            x+=2;
            sum+=x;
            cnt++;
            if(!(i%m)) 
            {
                printf("%d",sum/cnt);
                sum=0;
                cnt=0;
                if(i!=n) printf(" ");
                else flag=1;
            }
            //printf("\nsum %d   i %d    m %d\n",sum,i,!i%m);
        }
        if(flag==0) printf("%d",sum/cnt);
        printf("\n");
    }
    return 0;
}
```

## 1007

>Problem Description
>>给定一段连续的整数，求出他们中所有偶数的平方和以及所有奇数的立方和。
>
>Input
>>输入数据包含多组测试实例，每组测试实例包含一行，由两个整数m和n组成。
>
>Output
>>对于每组输入数据，输出一行，应包括两个整数x和y，分别表示该段连续的整数中所有偶数的平方和以及所有奇数的立方和。
你可以认为32位整数足以保存结果。
>
>Sample Input
>>1 3</br>
2 5
>
>Sample Output
>>4 28</br>
20 152</br>
</br>

``` c
#include<stdio.h>
int main()
{
    int m,n;
    while(~scanf("%d%d",&m,&n))
    {
        if(m>n)
        {
            int temp;
            temp=m;
            m=n;
            n=temp;
        }
        int odd=0,even=0;
        for(int b=m;b<=n;b++)
        {
            if(b&1!=0) odd+=b*b*b;
            else even+=b*b;
        }
        printf("%d %d\n",even,odd);
    }
    return 0;
}
```