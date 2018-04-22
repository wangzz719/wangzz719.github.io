---
layout: post
title: 快速排序算法
description: 快速排序算法
tags: algorithm, quicksort
---
#### 介绍
快速排序使用分治法策略来把一个序列分为两个子序列。

步骤为：

1. 从数列中挑出一个元素，称为"基准"（pivot），
2. 重新排序数列，所有比基准值小的元素摆放在基准前面，所有比基准值大的元素摆在基准后面（相同的数可以到任何一边）。在这个分区结束之后，该基准就处于数列的中间位置。这个称为分区操作。
3. 递归地把小于基准值元素的子数列和大于基准值元素的子数列排序。
4. 递归到最底部时，数列的大小是零或一，也就是已经排序好了。这个算法一定会结束，因为在每次的迭代中，它至少会把一个元素摆到它最后的位置去。

```go
package main

import "fmt"

// 快速排序
func quickSort(nums []int) []int {
	if len(nums) <= 1 {
		return nums
	}
	start, end := 0, len(nums)-1
	mid, current := nums[0], 1
	for start < end {
		if nums[current] > mid {
			nums[current], nums[end] = nums[end], nums[current]
			end--
		} else {
			nums[start], nums[current] = nums[current], nums[start]
			start++
			current++
		}
	}
	nums[start] = mid
	quickSort(nums[:start])
	quickSort(nums[start+1:])
	return nums
}

func main() {
	fmt.Println(quickSort([]int{2, 1, 3, 4, 0}))
}

```