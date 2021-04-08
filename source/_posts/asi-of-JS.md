---
title: JS自动分号插入机制
date: 2021-04-06 22:26:08
tags: JS
---

### 问题描述
前两天一时兴起, 复习过一遍十大排序, 快排和堆排都过了, 没想到卡在冒泡上, 并且卡了两个晚上..
代码:

``` bash
const arr=[1,2,8,5,1,7]
function bubble(arr){
    for(let i=0; i<arr.length-1; ++i){
        let flag=1
        for(let j=arr.length-1;j>i;--j){
            if(arr[j]<arr[j-1]){
                flag = 0
                [arr[j], arr[j - 1]] = [arr[j - 1], arr[j]]
            }
        }
        if(flag)
            return arr
    }
    return arr
}
console.log(bubble(arr))
```

但是结构赋值换个书写方式逻辑就正确了, 如下三种方式是都可以的

``` bash
function bubble(arr){
    for(let i=0; i<arr.length-1; ++i){
        let flag=1
        for(let j=arr.length-1;j>i;--j){
            if(arr[j]<arr[j-1]){
                flag = 0
                // OK
                // tmp=arr[j]
                // arr[j]=arr[j-1]
                // arr[j-1]=tmp

                // OK
                // const a =[arr[j-1], arr[j]];
                // [arr[j], arr[j-1]] = a; 

                // OK
                // const k = j - 1;
                // [arr[j], arr[k]] = [arr[k], arr[j]];
                
                // Fail
                // [arr[j], arr[j - 1]] = [arr[j - 1], arr[j]];
            }
        }
        if(flag)
            return arr
    }
    return arr
}
console.log(bubble(arr))
```

在使用解构赋值来交换a[j]和a[j-1]的时候, 没有语法错误, 但是排序逻辑出错, 想到后来感觉都是玄学问题..最后求助同学发现:**只是一个简单的分号问题**

因为JS无需加分号, 所以故意不加分号, 认为是语言特性的使用, 其实并没有了解全局

由于JS语言分号可以不写的特性, 引发的[自动分号插入机制](https://www.cnblogs.com/fsjohnhuang/p/4154503.html)问题

### 总结
一般来说，“(”、“[”、“/”、“+”、“-”，都会在上一行代码不加分号的情况下，与上一行代码相接，“++”、“--”在上下两行都不加分号的情况下，与下一行代码相接，如遇上了return才会在改行末尾加上分号。
-JS编码最好加分号-

