---
layout:     post
title:      Leetcode Contest
subtitle:   Weekly Diary
date:       2021-07-04
author:     Hanyu Chen
header-img: img/post-bg-miui6.jpg
catalog: true
tags:
    - Internship
---

## Weekly Contest 248

The first problem is too easy to write the solution.

This week I learned a new method to get the power calculation in $O(lgN)$ time complexity. In this week's contest, the third problem is to get $20^{n}$ when $n$ is extremely large (less than $10^{15}$).

The code could be constructed as below:

```java
public int quickly_pow(long base, long pow) {
  public static int mod = 1000000007;
  if (pow == 0) return 1;
  long res = 1;
  while (pow > 0) {
    if (pow % 2 == 1) {
      res = (res*base) % mod;
    }
    pow /= 2;
    base = (base*base) % mod;
  }
  return (int) res;
}
```

My performace of this contest is not really good, even the worst one in these weeks. Maybe I need more consideration before doing each problems, so that l can save much time on debugging the algorithm.