---
title: Manacher法
date: 2017-12-15
categories:
- Algorithm
- String
tags: 
- Algorithm
---

# 算法介绍

| 原字符串 | 转化后字符串 |
| :------: | :----------: |
| S        | T            |
| aaaba    | #a#a#a#b#a#  |
<!-- more -->
> Manacher算法用一个辅助数组Len[i]表示以字符T[i]为中心的最长回文字串的最右字符到T[i]的长度，比如以T[i]为中心的最长回文字串是T[l,r],那么Len[i]=r-i+1。

![image](http://img.blog.csdn.net/20141221160159348)

> Len数组有一个性质，那就是Len[i]-1就是该回文子串在原字符串S中的长度，至于证明，首先在转换得到的字符串T中，所有的回文字串的长度都为奇数，那么对于以T[i]为中心的最长回文字串，其长度就为2*Len[i]-1,经过观察可知，T中所有的回文子串，其中分隔符的数量一定比其他字符的数量多1，也就是有Len[i]个分隔符，剩下Len[i]-1个字符来自原字符串，所以该回文串在原字符串中的长度就为Len[i]-1。



# Code
```c++
LeetCode - 5 Longest Palindromic Substring

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