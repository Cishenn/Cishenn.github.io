---
title: 引用语义
date: 2021-04-11 11:19:30
tags: JS
---

#### 问题由来: 对基数排序中桶数组用Array.prototype.fill 初始化失败, 昨天在写桶排序的时候, 也遇到了类似的问题: 对桶数组用for of 语法初始化失败

##### radix排序
![radix](../assets/reference-sematics/radixSort.jpg)

##### 桶排序
![bucketSort](../assets/reference-sematics/bucketSort.jpg)
![fail](../assets/reference-sematics/fail.jpg)

可以猜到fill方法是失败的, 去验证一下:
##### fill方法
![fill方法](../assets/reference-sematics/fill.jpg)

##### 联想到for of 和 for in
![for-in](../assets/reference-sematics/for-in.jpg)
![for-of](../assets/reference-sematics/for-of.jpg)

##### 正常的for循环肯定是正确的
![for](../assets/reference-sematics/for.jpg)

##### 原因(待深究)
![refernce-sematics](../assets/reference-sematics/reference-sematics.jpg)