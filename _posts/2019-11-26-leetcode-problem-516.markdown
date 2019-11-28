---
layout: post
title:  "LeetCode 题解-516.longest-palindromic-subsequence"
date:   2019-11-26 10:39:33 +0800
---

对Leetcode 516.longest-palindromic-subsequence 题目的求解。

## Problem Description

Given a string s, find the longest palindromic subsequence's length in s. You may assume that the maximum length of s is 1000.

## Example 1

```
Input:
"bbbab"
Output:
4
```

## Example 2
```
Input:

"cbbd"
Output:
2
```

## Analysis

这道题目和第5题类似，不过第五题中我们考虑的时候包含区间头尾的回文串，而在这道题目中，我们需要考虑区间内的最长回文串，是一道很明显的动态规划题目，递归公式为
```
dp[i][j] = max(dp[i+1][j], dp[i][j-1]) if s[i] neq s[j]
dp[i][j] = max(dp[i+1][j], dp[i][j-1], dp[i+1][j-1]+2) if s[i] eq s[j]
```


## Solution 1: bfs with recursive call

```java
class Solution {
    public static int longestPalindromeSubseq(String s) {
        int l = s.length();
        if (l == 0) return 0;
        int dp[][] = new int [l][l];
        //int start = 0;
        for (int i = l-1; i >= 0; --i){
            for (int j = i; j < l ; ++j){
                //System.out.printf("%d %d\n", i, j);
                if (i == j) dp[i][j] = 1;
                //dp[i][j] = Math.max(dp[i][i+len-2], dp[i+1][i+len]);
                else if (s.charAt(i) == s.charAt(j)){
                    dp[i][j] = dp[i+1][j-1]+2;
                }
                else dp[i][j] = Math.max(dp[i][j-1], dp[i+1][j]);
            }
        }
        return dp[0][l-1];

    }
}
```
