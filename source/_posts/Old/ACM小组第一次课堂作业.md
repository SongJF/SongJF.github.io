---
title: ACM小组第一次课堂作业
author: SongJF
date: 2018-11-11 19:39:12
categories: ACM小组培训
tags:
---

# 1157

``` c
#include <stdio.h>
#include<algorithm>
using namespace std;

int main()
{
    int n;
    while(scanf("%d",&n)!=EOF)
    {
        int a[10001];
        //读入数列
        for(int i=0;i<n;i++) scanf("%d",&a[i]);
        
        //排序
        sort(a,a+n);
        //取中间那个值
        printf("%d\n",a[n/2]);
    }
}
```

# 1862
``` c
#include <stdio.h>
#include<string.h>
#include<algorithm>
using namespace std;

struct People
{
	int ID;
	char name[10];
	int score;
};

//据Id排序方案 
bool cmpById(People a,People b)
{
	return a.ID<b.ID;
}

//据姓名排序方案 
bool cmpByName(People a,People b)
{
	switch(strcmp(a.name,b.name))
	{
		case 1:
			return 0;
			break;
		case -1:
			return 1;
			break;
		case 0:
			//对姓名相同的的对象做Id比较处理 
			if(a.ID>b.ID) return 0;
			else return 1;
		default:
			return 0;
			break;
	}
}

//据分数排序方案 
bool cmpByScore(People a,People b)
{
	if(a.score==b.score)
	{
		//对分数相同的的对象做Id比较处理 
		if(a.ID<b.ID) return 1;
	}
	return a.score<b.score;
}


int main()
{
	int Count,Column;
	int n=1;
	while(scanf("%d%d",&Count,&Column)!=EOF)
	{
		//退出条件 
		if(!Count&&!Column) break;
		//读入数据 
		People person[100001];
		for (int i=0;i<Count;i++) scanf("%d%s%d",&person[i].ID,&person[i].name,&person[i].score);
		
		printf("Case %d:\n",n++);
		
		//根据输入的行号判断排序方案
		//结构体用sort排序需自定排序方案 
		switch(Column)
		{
			case 1:
				sort(person,person+Count,cmpById);
				break;
			case 2:
				sort(person,person+Count,cmpByName);
				break;
			case 3:
				sort(person,person+Count,cmpByScore);
				break;
			default:
				break;
		}
		
		//打印出结果 %06d补齐学号空位 
		for (int i=0;i<Count;i++) printf("%06d %s %d\n",person[i].ID,person[i].name,person[i].score);
	}
	return 0;
}
```