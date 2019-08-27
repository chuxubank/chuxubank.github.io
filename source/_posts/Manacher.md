---
title: Manacher
date: 2017-12-15
categories:
- Algorithm
- String
tags: 
- Manacher
toc: true
---

## 算法介绍

| 原字符串 | 转化后字符串 |
| :------: | :----------: |
|    S     |      T       |
|  aaaba   | #a#a#a#b#a#  |
<!-- more -->
Manacher算法用一个辅助数组 Len[i] 表示以字符 T[i] 为中心的最长回文字串的最右字符到 T[i] 的长度，比如以 T[i] 为中心的最长回文字串是 T[l,r] ,那么 Len[i]=r-i+1 。

Len数组有一个性质，那就是 Len[i]-1 就是该回文子串在原字符串S中的长度，至于证明，首先在转换得到的字符串T中，所有的回文字串的长度都为奇数，那么对于以 T[i] 为中心的最长回文字串，其长度就为 2*Len[i]-1 ，经过观察可知，T中所有的回文子串，其中分隔符的数量一定比其他字符的数量多1，也就是有 Len[i] 个分隔符，剩下 Len[i]-1 个字符来自原字符串，所以该回文串在原字符串中的长度就为 Len[i]-1 。

## 习题

### LeetCode - 5 Longest Palindromic Substring

 ``` c++ longestPalindrome https://leetcode-cn.com/problems/longest-palindromic-substring/ LeetCode
string longestPalindrome(string s) {
    string t = "$#";
    for (int i = 0; i < s.size(); ++i) {
        t += s[i];
        t += '#';
    }
    int p[t.size()] = {0}, id = 0, mx = 0, resId, resMx = 0;
    for (int i = 0; i < t.size(); ++i) {
        p[i] = mx > i ? min(p[2 * id - i], mx - i) : 1;
        //cout << i - p[i] << endl;
        while (i - p[i] > 0 && t[i + p[i]] == t[i - p[i]]) ++p[i];
        if (mx < i + p[i]) {
            mx = i + p[i];
            id = i;
        }
        if (resMx < p[i]) {
            resMx = p[i];
            resId = i;
        }
    }
    return s.substr((resId - resMx) / 2, resMx - 1);
}
```