---
title: 最大子序和
date: 2021-04-12 22:39:57
tags: algorithm
---
# 今日一题 最大子序和 5.3 简单

## 题目：
#### [53. 最大子序和](https://leetcode-cn.com/problems/maximum-subarray/)

给定一个整数数组 `nums` ，找到一个具有最大和的连续子数组（子数组最少包含一个元素），返回其最大和。
**示例:**
**输入:** [-2,1,-3,4,-1,2,1,-5,4],
**输出:** 6
**解释:** 连续子数组 [4,-1,2,1] 的和最大，为 6。
**进阶:**
如果你已经实现复杂度为 O(_n_) 的解法，尝试使用更为精妙的分治法求解。


给定一个整数数组 nums ，找到一个具有最大和的连续子数组（子数组最少包含一个元素），返回其最大和。


## 解题思路：
1.该思想来自于leetcode的题解：[https://leetcode-cn.com/problems/maximum-subarray/solution/hua-jie-suan-fa-53-zui-da-zi-xu-he-by-guanpengchn/](https://leetcode-cn.com/problems/maximum-subarray/solution/hua-jie-suan-fa-53-zui-da-zi-xu-he-by-guanpengchn/)
2.首先，使用max_n记录当前的最大值，使用sum来记录当前的子序和，当sum<=0时说明sum内包括的所有的值和对于后面的子序已经没有正面效果，当sum>0时说明可能对后面的子序求和有正面效果；
3.每次循环结尾时，比较当前的sum和max_n来获取当前的最大值并保留到max_n中，最后的max_n即为所求的最大子序和。


## 代码：
```cpp
class Solution {
public:
    int maxSubArray(vector<int>& nums) {
        int sum = 0;
        int max_n = nums[0];

        for(int i = 0; i < nums.size(); i++){
            if(sum > 0){
                sum += nums[i];
            }
            else{
                sum = nums[i];
            }

            max_n = max(sum, max_n); 
        }

        return max_n;
    }
};
```


## 思考：
1.推荐官方题解：[https://leetcode-cn.com/problems/maximum-subarray/solution/zui-da-zi-xu-he-by-leetcode-solution/](https://leetcode-cn.com/problems/maximum-subarray/solution/zui-da-zi-xu-he-by-leetcode-solution/)，如何使用分治法求解；

2. 0s代码，还是使用递归操作：
```cpp
class Solution {
public:
    int maxSubArray(vector<int>& nums) {
        int n = nums.size();

        int maxSum = nums[0], curSum = 0;
        for(int i = 0; i < n; i++) {
            curSum += nums[i];
            if(curSum > maxSum) maxSum = curSum;
            if(curSum <= 0) curSum = 0;
        }

        return maxSum;
    }
};
```
