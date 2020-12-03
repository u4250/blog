---
title: git多个账户在win10上的使用
date: 2020-12-03
categories:
 - other
tags:
 - git
 - 踩坑
---


## 前言
在本机已有一个账户的密钥时在向另一个账户的仓库推送时会出现权限的问题，所以需要在本地增加第二个账户的密钥
## 设置SSH公钥
找到.ssh文件夹（一般在c盘用户名文件夹下）使用git bash打开
```bash
ssh-keygen -t rsa -C "one@gmail.com"
```
:::tip
不要一路回车，在第一个对话的时候输入重命名（id_rsa_two），否则会和第一个账户生成的文件重名，导致意想不到的坏事发生！！  
:::
然后找到生成的.pub文件打开复制到github上
## 设置私钥
```bash
ssh-agent -s 
ssh-add ~/.ssh/id_rsa_two //名字要与上边输入的名字相同
```
在.ssh文件夹下新建config文件，写入以下内容
配置两个账户，注意name1与name2要与生成的文件同名
```bash
# work
Host work
   HostName github.com
   User git
   IdentityFile ~/.ssh/name1

# person
Host person
   HostName github.com
   User git
   IdentityFile ~/.ssh/name2
```
## 测试
```bash
ssh -T work
Hi work! You've successfully authenticated, but GitHub does not provide shell access.
```
成功！