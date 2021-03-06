---
title: "Leetcode算法 55.跳跃游戏"
date: 2019-09-26T17:49:50+08:00
draft: false
toc: true
categories: ["Leetcode算法"]
series: ["Leetcode算法"]
tags: ["go","面试","算法"]
toc: true
---

#### 简介

给定一个非负整数数组，你最初位于数组的第一个位置。

数组中的每个元素代表你在该位置可以跳跃的最大长度。

判断你是否能够到达最后一个位置。


**示例1:**

``` go
输入: [2,3,1,1,4]
输出: true
解释: 从位置 0 到 1 跳 1 步, 然后跳 3 步到达最后一个位置。
```

**示例2:**

``` go
输入: [3,2,1,0,4]
输出: false
解释: 无论怎样，你总会到达索引为 3 的位置。但该位置的最大跳跃长度是 0 ， 所以你永远不可能到达最后一个位置。
```

#### 解题思路

这题我们通过动态规划来做。

首先，我们先确定状态，最后一步一定是从[j-1]到[j](j为步数),也就是从前一个跳点，跳到终点。

因此，我们可以把这个问题，转换为子问题，判断倒数第二步是否可以跳到。

写出转移方程：f[j] && nums[j]+j >= lastIndex


``` go
func canJump(nums []int) bool {
	n := len(nums)
	f := make([]bool, n, n)
	f[0] = true

	for j := 1; j < n; j++ {
		f[j] = false
		for i := 0; i < j; i++ {
			// 如果上一个位置可以到达，并且上一个位置可以跳到当前的位置
			if f[i] && i+nums[i] >= j {
				f[j] = true
				break
			}
		}
	}
	return f[n-1]
}
```