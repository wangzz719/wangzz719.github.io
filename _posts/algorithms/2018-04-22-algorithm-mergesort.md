---
layout: post
title: 归并排序算法
description: 归并排序算法
tags: [linux awk]
---

### 介绍
归并排序算法是采用分治法（Divide and Conquer）的一个非常典型的应用。

算法通过将已有序的子序列合并，得到完全有序的序列；即先使每个子序列有序，再使子序列段间有序。

```go
package main

import "fmt"

// 归并排序
func mergeSort(nums []int) []int {
	numsLen := len(nums)
	if numsLen <= 1 {
		return nums
	}
	mid := numsLen / 2
	left := mergeSort(nums[:mid])
	right := mergeSort(nums[mid:])
	return merge(left, right)
}

// 合并两个有序序列
func merge(left []int, right []int) []int {
	leftLen := len(left)
	rightLen := len(right)

	var i, j int
	result := make([]int, 0)
	for i < leftLen && j < rightLen {
		if left[i] < right[j] {
			result = append(result, left[i])
			i++
		} else {
			result = append(result, right[j])
			j++
		}
	}

	result = append(result, left[i:]...)
	result = append(result, right[j:]...)
	return result
}

func main() {
	fmt.Println(mergeSort([]int{2, 1, 3, 0, 4}))
}
```