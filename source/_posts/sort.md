---
title: 排序算法
date: 2021-04-06 23:17:47
tags: Algorithm
---

#### 快排优化:
三数取中

``` bash
function midOfThree(arr){
        let low = 0;
        let high = arr.length - 1;
        let mid = Math.floor((high + low) >> 1);
        
        if (arr[mid] > arr[high])
                [arr[mid], arr[high]] = [arr[high], arr[mid]];
        if (arr[low] > arr[high])
                [arr[low], arr[high]] = [arr[high], arr[low]];
        if (arr[mid] > arr[low])
                [arr[mid], arr[low]] = [arr[low], arr[mid]];
        
        return arr[low];
}
```

- 较少数据(<10)且基本有序可以插入排序
- 同值聚集
- 尾递归

*快排记得arr[low], arr[high]和pivot比较时, 等于的情况要考虑到! 不然死循环

#### shell排序
注意第三循环的目标
1. gap: 是步长
2. i: 每个步长的组
3. j: 注意是gap间隔
