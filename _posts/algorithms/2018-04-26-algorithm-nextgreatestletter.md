---
layout: post
title: 查找字符数组中大于指定字符的最小字符
description: 查找字符数组中大于指定字符的最小字符
tags: algorithm, binarysearch
---

### 介绍
[744. Find Smallest Letter Greater Than Target](https://leetcode.com/problems/find-smallest-letter-greater-than-target/description/)

给定一个有序的字符数组 letters 和一个字符 target，要求找出 letters 中大于 target 的最小字符。letters 字符数组是循环数组。

```go
package main

import "fmt"

func nextGreatestLetter(letters []byte, target byte) byte {
	lettersLen := len(letters)
	l := 0
	h := lettersLen - 1
	for l <= h {
		mid := (l + h) / 2
		if letters[mid] <= target {
			l = mid + 1
		} else {
			h = mid - 1
		}
	}
	if l < lettersLen {
		return letters[l]
	}
	return letters[0]
}

func main() {
	lts := []byte{'c', 'f', 'j'}
	fmt.Printf("%c\n", nextGreatestLetter(lts, 'd'))
}

```