---
title: Hexo部署后，CNAME 失效的问题
date: 2021-04-07 11:37:58
tags: debug
---

每一次deploy就会清空github Page:
![alt Github Page](/assets/githubpage-url-remove.png)

当在本地source文件夹里建立一个CNAME，里面输入你的域名地址（注意：只能输入一个！例如输入：aliyun.com），或者在GitHub仓库上把该文件下载下来，将其放置在source文件夹目录下。这样，在进行之后的更新部署就不需要进行重新设定了