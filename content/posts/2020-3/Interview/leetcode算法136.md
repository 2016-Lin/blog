---
title: "Leetcode算法 136. 只出现一次的数字"
date: 2020-03-13T11:10:50+08:00
draft: false
toc: true
categories: ["Leetcode算法"]
series: ["Leetcode算法"]
tags: ["go","面试","算法","位运算"]
toc: true
---

#### 136. 只出现一次的数字

给定一个非空整数数组，除了某个元素只出现一次以外，其余每个元素均出现两次。找出那个只出现了一次的元素。

**说明:**

``` txt
你的算法应该具有线性时间复杂度。 你可以不使用额外空间来实现吗？

```

**示例1：**
``` golang
输入: [2,2,1]
输出: 1
```

**示例2：**

``` golang
输入: [4,1,2,1,2]
输出: 4
```

#### 解题

使用异或
1.交换律：a ^ b ^ c <=> a ^ c ^ b
2.任何数于0异或为任何数 0 ^ n => n
3.相同的数异或为0: n ^ n => 0
var a = [2,3,2,4,4]
2 ^ 3 ^ 2 ^ 4 ^ 4等价于 2 ^ 2 ^ 4 ^ 4 ^ 3 => 0 ^ 0 ^3 => 3


``` golang
func singleNumber(nums []int) int {
	n := 0
	for i := range nums {
		n ^= nums[i]
	}
	return n
}

```