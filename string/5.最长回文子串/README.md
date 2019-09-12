# 最长回文子串
给定一个字符串 s，找到 s 中最长的回文子串。你可以假设 s 的最大长度为 1000。

示例 1：
```
输入: "babad"
输出: "bab"
注意: "aba" 也是一个有效答案。
```

示例 2：
```
输入: "cbbd"
输出: "bb"

```

```go
func longestPalindrome(s string) string {
    
}
```

## 解题思路
动态规划，使用一个二维数组标记[i,j]是不是一个回文串

![状态数组](./dp.svg?raw=true)
[![alt](./dp.svg)](./dp.svg&sanitize=true)

## 
