---
title: asi-of-JS
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


在使用解构赋值来交换a[j]和a[j-1]的时候, 没有语法错误, 但是排序逻辑出错.

因为JS无需加分号, 所以故意不加分号, 认为是语言特性的使用, 其实并没有了解全局
