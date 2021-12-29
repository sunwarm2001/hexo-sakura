---
title: BFS模板
author: sunwarm
avatar: https://cdn.jsdelivr.net/gh/sunwarm2001/cdn/img/avatar/sunwarm2001.jpg
authorLink: 
categories: 技术
date: 2020-11-5 23:10:48
comments: true
tags:   
 - 算法
 - 模板
keywords: bfs
description: 走迷宫
photos: https://cdn.jsdelivr.net/gh/sunwarm2001/cdn/img/myown/15.jpg
---

## BFS模板
>解决问题：最优解问题，如最短路径  
---
### BFS思路：队列queue
```
初始化队列Q
Q={起点s}
标记起点s已被访问
while (Q非空)
{
	取出Q队首元素u，同时把u弹出队列。
	if（u==目标状态）
	{.......}
	求出所有与u相邻元素v
	{
		if(v满足条件且未被访问)
			{ v入队列，标记v已被访问 }
	}
}
```
---
### 题目：
走迷宫：给定一个N*M方格的迷宫，其中`.`代表可通过，`*`代表障碍物。问: 每个方格最多经过1次，有多少种从**左上角**到**右下角**的方案。在迷宫中移动有上下左右四种方式，每次只能移动一个方格。数据保证起点上没有障碍。
```
#include<iostream>
#include<queue>
using namespace std;
int  map[105][105];			//定义地图
bool vis[105][105];			//判断某点是否走过
//定义上{-1,0}、下{1,0}、左{0,-1}、右{0,1}四个方向
//注：因为地图是数组来创建的，当往上走时是行-1，列不变，因此为{-1,0}。而不是坐标系中的{0,-1}
int  dir[4][2] = { {-1,0},{1,0},{0,-1},{0,1} };
int n, m;
//定义图上的坐标点
class Node
{
public:
	int x, y, d;	//x：行   y：列   d:走过的长度
	Node(int a,int b,int c):x(a),y(b),d(c){}
};

//检查坐标是否在地图中
bool check(int i, int j)
{
	if (i > 0 && i <= n && j > 0 && j <= m)
		return true;
	else
		return false;
}

void bfs()
{
	queue<Node> p;
	p.push(Node(1, 1, 0));		        //起点（1,1）
	vis[1][1] = true;			//表示起点（1,1）已被走过
	while (!p.empty())
	{
		Node next = p.front();
		p.pop();
		if (next.x == n && next.y == m)		//当取出的是终点时，则输出走过的长度
		{
			cout << next.d;
			return;
		}
		for (int i = 0; i < 4; i++)			//将该点上下左右四个方向都走一遍
		{
			int dx = next.x + dir[i][0];
			int dy = next.y + dir[i][1];
			if (check(dx, dy) && map[dx][dy] == 0 && vis[dx][dy] == false)
			{
				vis[dx][dy] = true;
				p.push(Node(dx, dy, next.d + 1));	
			}
		}
	}
}
int main()
{
	cin >> n >> m;
	for (int i = 1; i <= n; i++)
		for (int j = 1; j <= m; j++)
			cin >> map[i][j];
	bfs();
	return 0;
}
```