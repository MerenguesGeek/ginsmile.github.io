---
layout: post
title: "我的Git常用命令"
date: 2013-09-20 16:50
comments: true
categories: 
---


使用Git开发已经有一段时间了，这里我总结了一下常用的Git命令。

设置
-----------------------------
{% img right /images/pic/git_logo.png 130 130 'welcome' 'welcome' %}   
设置邮箱和用户名

    git config --global user.email "xu.jin.smile@gmail.com"
    git config --global user.name "GinSmile"
生成SSH Key

    ssh-keygen -t rsa -C "example@163.com"
    ....然后提示输入密码什么的

<!--more-->
创建
-----------------------------
初始化本地库

    git init
克隆远程版本库

    git clone git@github.com:GinSmile/Algorithms.git
添加远程分支(添加Algorithm项目的dev分支到本地)

    git remote add dev git@github.com:GinSmile/Algorithms.git
查看远程分支

    git remote -v
    
提交
----------------------------------
提交

    git add .
    git commit -m "some comment"
更改上次提交的comment注释

    git commit -amend "new comment"
查看状态，即查看那些文章被修改了

    git status
查看提交的历史记录
    
    git log


删除
-----------------------------------
从当前跟踪列表中移除文件，并完全删除

    git rm Readme.md
仅仅在暂存区删除，不再跟踪该文件，并在目录中保留

    git rm –cached Readme.md
    



分支
-------------------------------------
创建一个名为dev的分支

    git branch dev
切换到dev分支
    
    git checkout dev

创建并切换到dev分支（等同于以上两个命令）
    
    git checkout -b dev
    

    

合并
----------------------------------
从远程库中拉去最新文件，并自动合并

    git pull
合并分支（当前分支为master，要合并dev的更改）

    git merge dev
    


忽略
-------------------------------
即.gitignore文件，可忽略文件夹和文件
忽略文件夹

    bin
忽略文件

    *.c
    
    
最近发现一张特别棒的Git 命令思维导图，特拿来备份，感谢原作者。点击查看大图
{% imgpop /images/pic/git.png 10% Git Command %}

参考资料：
---------------------------------
> - [Git Guide](http://rogerdudler.github.io/git-guide/index.zh.html)
> - [Pro Git](https://code.csdn.net/help/CSDN_Code/code_support/Progit_Index)
> - [开源中国社区](http://www.oschina.net/question/54100_74533)

