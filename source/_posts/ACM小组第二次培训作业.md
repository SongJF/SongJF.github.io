---
title: ACM小组第二次培训作业
author: SongJF
date: 2018-11-17 21:19:30
categories: ACM小组培训
tags:
---

## [1001](http://acm.hdu.edu.cn/diy/diy_previewproblem.php?cid=34364&pid=1001)
```c
#include<stdio.h>
#include<algorithm>
using namespace std;

int main()
{
	int n;
	while(scanf("%d",&n)!=EOF)
	{
		while(n--)
		{
			//对输入进行处理 
			int num,a[12];
			scanf("%d",&num);
			for(int i=0;i<num;i++) scanf("%d",&a[i]);
			
			//从大到小排序排序 
			sort(a,a+num);
			
			//打印出第二小的数 
			printf("%d\n",a[1]);
		}
	}
	
	return 0;
} 
```

## [1002](http://acm.hdu.edu.cn/diy/diy_previewproblem.php?cid=34364&pid=1002)
```c

#include<stdio.h>
#include<string.h>
int main()
{
    char a[202],m=0;
    int b=0,c=0,flag=0;
    while(scanf("%s",&a)!=EOF)
    {
        b=strlen(a);
        m=a[0];
        for(int i=1;i<=b-1;i++)
        {
            if(m<=a[i])
            {
                m=a[i];
                c=i;
            }        
        }
        for(int i=0;i<b;i++)
        {
            printf("%c",a[i]);
            if(a[i]==m) printf("(max)");
            if(i==b-1) printf("\n");
        }
    }
    return 0;
} 
```

## [1003](http://acm.hdu.edu.cn/diy/diy_previewproblem.php?cid=34364&pid=1003)
```c
#include<stdio.h>
#include<math.h>
int main()
{
    int n,a[100]={0};
    while(scanf("%d",&n)!=EOF &&n!=0)
    {
        for(int i=0;i<n;i++)
          scanf("%d",&a[i]);
        int tem;
        for(int i=0;i<n;i++)
        {
            for(int j=0;j<n-i;j++)
            {
                if(abs(a[j])<abs(a[j+1])) 
                {
                    tem=a[j+1];
                    a[j+1]=a[j];
                    a[j]=tem;
                }
            }
        }
        for(int i=0;i<n;i++)
        {
            printf("%d",a[i]);
            if(i!=n-1) printf(" "); 
        }
        printf("\n");
    }
    return 0;
}
```

## [1004](http://acm.hdu.edu.cn/diy/diy_previewproblem.php?cid=34364&pid=1004)
```c
#include<stdio.h>
#include<algorithm>
#include<string.h>
using namespace std;

int main()
{
	char str[1005];
	while(scanf("%s",&str)!=EOF)
	{
		int num=0;
		long long a[1005]={0};
		
		//初始化分词指针 
		char *point=strtok(str,"5");
		while(point)
		{
			//string转int 
			a[num++]=atoi(point);
			
			//进行下一个分词
			point=strtok(NULL,"5");
		}
		
		//排序 
		sort(a,a+num);
		
		//照格式输出数据 
		for(int i=0;i<num;i++) 
		{
			printf("%d",a[i]);
			if(i!=num-1) printf(" ");
		}
		printf("\n");
	}
}
```

## [1005](http://acm.hdu.edu.cn/diy/diy_previewproblem.php?cid=34364&pid=1005)
```c
#include<stdio.h>
#include<math.h> 
#include<string.h>
using namespace std;
//对浮点数二分逼近时需要 
#define def 1e-10

//公共变量在前面声明 
int n,k;
double num[10005]; 

//判断按照此方案切绳子是否符合要求 
bool isOK(double mid)
{
	int count=0;
	//对每段绳子进行切割 
	for(int i=0;i<n;i++)
    {
        count+=(int)(num[i]/mid);
    }
    //总数达标即返回真 
	if(count>=k) return true;
	else return false;
}

double findmid(double start,double end)
{
	double mid;
	//设定二分退出条件 
	while(fabs(start-end)>def)
	{
		mid=(start+end)/2;
		
		//用二分减少需要判定方案是否合法的次数 
		if(isOK(mid)) start=mid;
		else end=mid;
	} 
	return mid;
}

int main()
{
	while(scanf("%d%d",&n,&k)!=EOF)
	{
		if(n==0&&k==0) break;
		//对数组置零 
		memset(num,0,sizeof(num));
		double sum=0;
		//读入数据 
		for(int i=0;i<n;i++)
		{
			scanf("%lf",&num[i]);
			sum+=num[i];
		} 
		
		printf("%.2f\n",findmid(0,sum/k));
	}
	return 0;
} 
```

## [1006](http://acm.hdu.edu.cn/diy/diy_previewproblem.php?cid=34364&pid=1006)
```c
#include<stdio.h>
#include<algorithm>
using namespace std;
int main()
{
    int t;
    scanf("%d",&t);
    while(t--)
    {
        int n,a[1000];
        scanf("%d",&n);
        for(int i=0;i<n;i++) scanf("%d",&a[i]);
        sort(a,a+n);
        for(int i=0;i<n;i++) 
        {
            printf("%d",a[i]);
            if(i!=n-1) printf(" ");
        }
        printf("\n");
    }
    return 0;
}
```