---
title: DFS模板
author: sunwarm
avatar: https://cdn.jsdelivr.net/gh/sunwarm2001/cdn/img/avatar/sunwarm2001.jpg
authorLink: 
categories: 技术
date: 2020-11-5 23:10:43
comments: true
tags:   
 - 算法
 - 模板
keywords: dfs
description: 全排列 与 n皇后
photos: https://cdn.jsdelivr.net/gh/sunwarm2001/cdn/img/myown/34.jpg
---

## DFS模板
>解决问题：所有解问题，或连通性问题
---
### DFS思路：递归
```
void dfs(int step)
{
	判断边界if()
	{
		相应操作
	}
		尝试每一种可能for()
	{
		   满足条件if()
		   标记  == true;
		   继续下一步:dfs(step + 1)
		   恢复初始状态（回溯的时候要用到）
	}
}
```
---
### 题目
1. 全排列：输出自然数 1 到 n 所有不重复的排列，即 n 的全排列，要求所产生的任一数字序列中不允许出现重复的数字
- 递归实现
```
#include<iostream>
using namespace std;
const int N = 10;
int num[N],n;
bool vis[N];
void dfs(int u)
{
	if (u > n)
	{
		for (int i = 1; i <= n; i++)
			cout << num[i] << ' ';
		cout << endl;
		return;
	}
	for (int i = 1; i <= n; i++) {
		if (!vis[i]) {
			num[u] = i;
			vis[i] = true;
			dfs(u + 1);																					
			vis[i] = false;
		}
	}
	return;
}
int main()
{
	cin >> n;
	dfs(1);

	return 0;
}
```
- 借助STL的next_permutation(arr, arr + size)来实现;
```
//STL中的next_permutation(arr, arr + size);
#include<iostream>
#include<algorithm>
#include<vector>
using namespace std;
int main()
{
	int n;
	vector<int> v;
	cin>>n;
	for(int i=1;i<=n;i++)
		v.push_back(i);
	//若用while()语句则直接执行next_permutation（）函数，会少初始情况
	do
	{
		for(auto x:v)
			cout<<x<<' ';
		cout<<endl;
	}while(next_permutation(v.begin(),v.end()));	//记得有分号
	return 0;
}
```

2. n皇后问题：在一个N*N的棋盘上放置N个皇后，使这N个皇后不能在同一行、同一列、同一斜线上。
```
#include<iostream>
using namespace std;
int n;
const int Max = 100;			//注意把数组开大：因为后面有b[row-j+n]，不开大可能超出数组范围。
bool col[Max], a[Max], b[Max];	//col：列，a：斜线，b：斜线
char re[Max][Max];
void dfs(int row)
{
	if (row == n)
	{
		for (int j = 0; j < n; j++)
			cout << re[j]<<endl;
		cout << endl;
		return;
	}

	for (int j = 0; j < n; j++)
	{
		if (!col[j] && !a[row + j] && !b[row-j + n])	//b[row-j+n]加了n之后，row-j+n和j-row+n效果一样
		{
			re[row][j] = 'Q';
			col[j] = a[row + j] = b[row-j + n] = true;
			dfs(row + 1);
			col[j] = a[row + j] = b[row-j + n] = false;
			re[row][j] = '.';							//别忘记复原
		}
	}
	return;
}
int main()
{
	cin >> n;
	for (int i = 0; i < n; i++)
		for (int j = 0; j < n; j++)
			re[i][j] = '.';
	dfs(0);
	return 0;
}
```