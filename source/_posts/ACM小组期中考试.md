---
title: ACM小组期中考试
author: SongJF
date: 2018-12-02 15:35:36
categories: ACM小组培训
tags:
---

[前往问题](http://acm.hdu.edu.cn/diy/contest_show.php?cid=34513)

<!-- TOC -->autoauto- [1001](#1001)auto- [1002](#1002)auto- [1003](#1003)auto- [1004](#1004)auto- [1005](#1005)auto- [1006](#1006)auto- [1007](#1007)autoauto<!-- /TOC -->

<!--more-->

## 1001

```c
#include<stdio.h>
#include<algorithm>
using namespace std;

int main()
{
	int n;
	while(scanf("%d",&n))
	{
		long long a,b;
		long long ans=0;
		for(int i=1;i<=n;i++) 
		{
			scanf("%lld %lld",&a,&b);
			//对每个探险家选择其最低的出价
			ans+=min(a,b); 
		}
		printf(">>%d\n",ans);
	} 
	return 0;
}
```

## 1002

```c
#include<stdio.h>
#include<string.h>
#include<queue>
#include<algorithm>
#include<iostream>
#include<stdlib.h>
#define inf 0x3f3f3f3f
using namespace std;
const int maxn=200010;//点数 
const int maxm=800010;//边数

struct node{
	int v,next,cap,flow;
}edge[maxm];
int cnt;
int head[maxn];
int cur[maxn],d[maxn];// 当前弧下标   结点到汇点弧长 
int p[maxn],gap[maxn];////可增广路上的上一条弧   gap优化
int ss[maxn];//保存路径

void init(){
	cnt=-1;
	memset(head,-1,sizeof(head));
} 
void debug(int k){
	int i,j;
	printf("\n");
	for (i=0;i<=k;i++) 
	for (j=head[i];j!=-1;j=edge[j].next) 
        
        printf("%d %d %d\n",i,edge[j].v,edge[j].flow);
}

void add(int u,int v,int w,int rw){
	cnt++;
	edge[cnt].v=v;
	edge[cnt].next=head[u];
	edge[cnt].cap=w;
	edge[cnt].flow=0;
	head[u]=cnt;
	cnt++;
	edge[cnt].v=u;
	edge[cnt].next=head[v];
	edge[cnt].cap=rw;
	edge[cnt].flow=0;
	head[v]=cnt;
}

void bfs(int k){
	int v,i;
	int u;
	memset(gap,0,sizeof(gap));
	memset(d,-1,sizeof(d));
	d[k]=0;
	gap[0]++;
	queue<int> q;
	q.push(k);
	while(q.empty()==false){
		u=q.front();q.pop();
		for (i=head[u];i!=-1;i=edge[i].next){
			v=edge[i].v;
			if (d[v]==-1) {
				d[v]=d[u]+1;
				gap[d[v]]++;
				q.push(v);
			}
		}
	}
}

int sap(int s,int t,int N){
	int i;
	bfs(t);
	memcpy(cur,head,sizeof(head));
	int top=0;
	int u=s;
	int ans=0;
	while(d[s]<N){
		if (u==t){
			int min=inf;
			int inser;
			for (i=0;i<top;i++){
				if (min>=edge[ss[i]].cap-edge[ss[i]].flow){
					min=edge[ss[i]].cap-edge[ss[i]].flow;
					inser=i;//这跟管子是满流了 
				}
			}
			for (i=0;i<top;i++){
				edge[ss[i]].flow+=min;
				edge[ss[i]^1].flow-=min;
			} 
			ans+=min;
			top=inser;
			u=edge[ss[top]^1].v;//u为满流的那个结点 也就是那根管子的倒管子的终点
			continue;
		}
		bool ok=false;
		int v;
		for (i=cur[u];i!=-1;i=edge[i].next){ 
			v=edge[i].v;
			if (edge[i].cap-edge[i].flow>0&&d[v]+1==d[u]){
				ok=true;
				cur[u]=i;
				break;
			}//u后 添加了一条下标为i的弧 
		}
		if(ok==true){
			ss[top]=cur[u];
			top++;
			u=v;
			continue;
		}
		//如果这条路已经走不通了，那么撤退
		int min=N;
		for (i=head[u];i!=-1;i=edge[i].next)
		  if (edge[i].cap-edge[i].flow>0&&d[edge[i].v]<min){
		  	min=d[edge[i].v];
		  	cur[u]=i;
		  }
		gap[d[u]]--;
		if (gap[d[u]]==0) return ans;
		d[u]=min+1;
		gap[d[u]]++;
		if (u!=s) {
			top--;
			u=edge[ss[top]^1].v;
			
	}
	}
	return ans;
}

int main()
{
	int n,m,x,y,z;
	while(scanf("%d%d",&n,&m)!=EOF)
	{
		init();
		for(int i=0;i<n;i++) 
		{
			scanf("%d %d",&x,&y);
			add(0,i,x,0);
			add(i,n+1,y,0);
		}
		for(int i=0;i<m;i++) 
		{
			scanf("%d %d %d",&x,&y,&z);
			add(x,y,z,z);
		} 
		
		int ans=sap(0,n+1,n+2);
		printf("%d\n",ans);
	}
	return 0;
}
```

## 1003

```c
#include<stdio.h>

int main()
{
	int t;
	scanf("%d",&t);
	while(t--)
	{
		__int64 n,k,s;
		scanf("%I64d%I64d%I64d",&n,&k,&s);
		printf("%d\n",(n+k-1)/k*s);
	} 
	return 0;
}
```

## 1004

```c
#include<stdio.h>
#include<string.h>

char keyName[] = "nowhere";

int main()
{
    char givenStr[1005];
    //这里的字符串要读入空格 所以使用gets 同时文件尾标记为NULL 
    while(gets(givenStr)!=NULL)
    {
        if(strstr(givenStr,keyName)) printf("%s\n","nowhere is coming!");
        else printf("%s\n","nowhere is sleeping!");
    }
    return 0;
} 
```

## 1005

```c
#include<stdio.h>
#include<string.h>
#include<math.h>
#include<algorithm>
using namespace std;

int main()
{
	int t;
	scanf("%d",&t);
	while(t--)
	{
		int n,k;
		int Sad[1005],SadSum=0,MaxSad;
		scanf("%d%d",&n,&k);
		for(int i=0;i<n;i++) scanf("%d",&Sad[i]);
		scanf("%d",&MaxSad);
		sort(Sad,Sad+n);
		for(int i=0;i<k;i++) SadSum+=Sad[i];
		if(SadSum<MaxSad) printf("Yes\n");
		else printf("No\n");
	}
	return 0;
}
```

## 1006

```c
#include<stdio.h>
#include<string.h>
#include<math.h>
#include<algorithm>
using namespace std;

struct Point{
	double x;
	double y;
};

double Distance(Point i,Point j)
{
	return sqrt((i.x-j.x)*(i.x-j.x)+(i.y-j.y)*(i.y-j.y));
} 

int main()
{
	int t;
	scanf("%d",&t);
	while(t--)
	{
		//利用结构体保存位置信息 并读入顺序 
		Point s,a,b,e;
		scanf("%lf%lf",&s.x,&s.y);
		scanf("%lf%lf",&a.x,&a.y);
		scanf("%lf%lf",&b.x,&b.y);
		scanf("%lf%lf",&e.x,&e.y);
		
		//走的路线只有两种方案 枚举即可 
		double planA=Distance(s,a)+Distance(a,b)+Distance(b,e);
		double planB=Distance(s,b)+Distance(b,a)+Distance(a,e);
		
		printf("%.4lf\n",min(planA,planB)); 
	} 
	return 0;
}
```

## 1007

```c
#include<stdio.h>
#include<string.h>
#include<math.h>
#include<algorithm>
using namespace std;

int a[1005][1005];

int main()
{
	int m,n;
	
	while(scanf("%d%d",&n,&m)!=EOF)
	{
		memset(a,0,sizeof(a));
		for(int i=0;i<n;i++)
		{
			for(int j=0;j<m;j++)
			{
				scanf("%d",&a[i][j]);
			}
		}
		
		
		//换向输出
		for(int i=0;i<m;i++)
		{
			for(int j=0;j<n;j++)
			{
				printf("%d",a[n-j-1][i]);
				//一个数输出完毕时空格 
				if(j!=n-1) printf(" "); 
			}
			//每行输出结束换行 
			printf("\n");
		} 
		//矩阵输出结束空行 
		printf("\n");
		
		
	}
	
	return 0;
}
```