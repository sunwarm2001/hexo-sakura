---
title: markdown语法
author: sunwarm
avatar: https://cdn.jsdelivr.net/gh/sunwarm2001/cdn/img/avatar/sunwarm2001.jpg
authorLink: 
categories: 技术
date: 2020-11-5 23:10:43
comments: true
tags:   
 - markdown
 - 阅读
keywords: markdown
description: markdown语法大全
photos: https://cdn.jsdelivr.net/gh/sunwarm2001/cdn/img/myown/10.jpg
---


# markdown语法
---

## 一.&nbsp;标题  
- 语法： '#' 标记1-6级标题，一级标题对应一个'#'，以此类推  
- 用法： '#' 后必须加个空格  
- 例子：
```
# 一级标题
## 二级标题
### 三级标题
.......
```
- 效果如下：
# 一级标题
## 二级标题
### 三级标题

---

## 二.&nbsp;空格和换行
#### 1. 空格  
markdown的空格有两种方法：  
- 手动输入(\&nbsp;)
- 使用全角空格(shift+空格)  

#### 2. 换行  
markdown的换行有三种方法
- 在尾部使用两个空格 + 回车 
- 使用标签\<br>
- 使用两下回车 （ 此方法会多空一行）
---

## 三.&nbsp;字体
#### 1.加粗：文字用 '**' 包起来
#### 2.斜体：文字用'*'包起来
#### 3.斜体加粗：文字用'***'包起来
#### 4.删除线：文字用'~~'包起来  
例子：
```
**加粗的文字**
*斜体的文字*
***斜体加粗的文字***
~~加删除线的文字~~
```
效果如下：
**加粗的文字**  
*斜体的文字*  
***斜体加粗的文字***  
~~加删除线的文字~~  

---

## 四.&nbsp;分隔线、下划线、引用
#### 1. 分隔线：使用三个或以上的 减号(-)、星号(*)、底线(_)
#### 2.下划线：通过\<u>标签实现
- 例子：```<u>文字</u>```
- 效果：<u>文字</u>

#### 3.引用：在引用的文字前加 >
- 注：引用可以嵌套，如加多个 >
- 例子： 
    ```
    >引用1
    >>引用2
    >>>引用3
    ```
- 效果：
    >引用1
    >>引用2
    >>>引用3
---

## 五.&nbsp;列表
#### 1. 无序列表  
- 用法：使用星号(`*`)、加号(`+`)、减号(`-`)中的任一个作为列表标记，空一格在填写内容
- 例子：

```
- one
- two
- three
```

#### 2. 有序列表  
- 用法：数字加上`.`并空一格在填写内容   
- 例子：

```
1. 列表one
2. 列表two
3. 列表three
```


#### 3. 列表嵌套
在下一级前使用tab键（或者空三个）
例子：
```
1. The first   
    - The first of one
    - The first of two
2. The second   
    - The second of one
    - The second of two 
- 无序1   
    - 无序1.1  
       - 无序1.1.1  
```
效果：
1. The first   
    - The first of one
    - The first of two
2. The second   
    - The second of one
    - The second of two 
- 无序1   
    - 无序1.1  
       - 无序1.1.1  
---

## 六.&nbsp;代码块
#### 1. 单行代码
- 用法：用一个反引号(`)包起来
- 例子
```
`printf()`
```
- 效果  
`printf()`

#### 2. 代码块
- 用法：两边用三个反引号包起来，并且每边都独占一行
- 例子：
\```  
代码1...  
代码2...  
代码3...  
\```
- 效果
```  
代码1...  
代码2...  
代码3...  
```

---

## 七.&nbsp;链接
- 用法：
    - \[标题]("超链接地址")
    - <链接地址>
- 例子：
```
[百度](https://www.baidu.com)
[简书](https://www.jianshu.com)
<https://www.taobao.com>
```
[百度](https://www.baidu.com)  
[简书](https://www.jianshu.com)  
<https://www.taobao.com>

---
## 八.&nbsp;图片 
- 用法：\!\[alt](图片地址   "title")    
    - 开头是一个感叹号(!)    
    - alt：显示在图片下面的文字，相当于对图片内容的解释。  
    - title：图片的标题，当鼠标移到图片上时显示的内容。title可加可不加

- 例子
```
![冰冻柠檬](https://cdn.jsdelivr.net/gh/sunwarm2001/cdn@1.1/img/myown/10.jpg)
```

- 效果
!["冰冻柠檬"](https://cdn.jsdelivr.net/gh/sunwarm2001/cdn@1.1/img/myown/10.jpg)
---

