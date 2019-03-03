---
title: Greast Common Divisor
date: 2019-03-02 09:17:32
categories:
  - Algorithm
  - Number-Theoretic
tags:
  - Algorithm
  - GCD
  - LCM
toc: true
---
## 算法介绍

辗转相除法（欧几里得算法 `Euclid's algorithm`）的关键在于如下恒等式：
$$
\gcd(a, b) = \gcd(b, a \bmod b)
$$

<!-- more -->

它与边界条件 $\gcd(a, 0) = a$ 一起构成了
```c++
int gcd(int a, int b)
{
    return b == 0 ? a : gcd(b, a % b);
}
```
由于在递归调用时第二个参数的值单调递减且非负，故总能终止，且递归层数不超过 $4.785\lg{N}+1.6723, N = \max \lbrace a, b \rbrace$ 。

而让 `gcd` 递归层数最多的是 $\gcd(F_n, F_{n-1})$，$F_n$ 是 `Fibonacci` 数列。

利用最大公约数 `gcd` 还可以求出最小公倍数 `lcm` 。可以由唯一分解定理得到。
设
$$
\begin{aligned}
a &= p_1^{e_1} p_2^{e_2} \cdots p_r^{e_r} \\\\
b &= p_1^{f_1} p_2^{f_2} \cdots p_r^{f_r}
\end{aligned}
$$

则

$$
\begin{aligned}
\gcd(a, b) &= p_1^{\min \lbrace e_1, f_1\rbrace} p_2^{\min \lbrace e_2, f_2\rbrace} \cdots p_r^{\min \lbrace e_r, f_r\rbrace}\\\\
\operatorname{lcm}(a, b) &= p_1^{\max \lbrace e_1, f_1\rbrace} p_2^{\max \lbrace e_2, f_2\rbrace} \cdots p_r^{\max \lbrace e_r, f_r\rbrace}
\end{aligned}
$$

故

$$
\gcd(a, b) \times \operatorname{lcm}(a, b) = a \times b
$$

由此
```c++
int lcm(int a, int b)
{
    return a / gcd(a, b) * b;
}
```
注意不要写成 `a * b / gcd(a, b)` 因为 `a * b` 可能溢出。