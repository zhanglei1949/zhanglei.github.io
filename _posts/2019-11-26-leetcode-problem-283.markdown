---
layout: post
title:  "LeetCode 题解-283. Move Zeroes"
date:   2019-12-01 14:03:12 +0800
---

对Leetcode 283. Move Zeroes 题目的求解。

## Problem Description

Given an array nums, write a function to move all 0's to the end of it while maintaining the relative order of the non-zero elements.

## Example 1

```
Input: [0,1,0,3,12]
Output: [1,3,12,0,0]
```

## Note

- You must do this in-place without making a copy of the array.
- Minimize the total number of operations.

## Analysis

题目要求我们要in-place,所以我们不能开辟新的空间．这道题我们使用快慢指针．快指针指向当前元素，慢指针指向新数组的当前元素．

## Solution

```java
class Solution {
    public static void moveZeroes(int[] nums) {
        int cur = 0;
        for (int i = 0; i < nums.length; ++i){
            if (nums[i] != 0){
                nums[cur++] = nums[i];
            }
        }
        for (int i = cur; i < nums.length; ++i){
            nums[i] = 0;
        }
    }
}
```
