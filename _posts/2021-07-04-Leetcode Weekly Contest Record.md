---
layout:     post
title:      Leetcode Contest
subtitle:   Weekly Diary
date:       2021-07-04
author:     Hanyu Chen
header-img: img/post-bg-miui6.jpg
catalog: true
tags:
    - Leetcode
---

## Weekly Contest 248

The first problem is too easy to write the solution.

This week I learned a new method to get the power calculation in $$O(lgN)$$ time complexity. In this week's contest, the third problem is to get $$20^{n}$$ when $$n$$ is extremely large (less than $$10^{15}$$).

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



## Biweekly contest 56

The second problem is a classic BFS problem. Remember to use a $visited$ vector to record the visited paths. The code below could be the model of BFS algorithm:

``````java
class Solution {
    int res = Integer.MAX_VALUE;
    
    public int nearestExit(char[][] maze, int[] entrance) {
      	// Directions
        int[] directions = new int[] {0, 1, 0, -1, 0};
      	// Use queue to store the nodes of each depth
        Queue<int[]> queue = new LinkedList<>();
        queue.offer(entrance);
        int steps_num = 0;
      	// Use a 2D-vector to record the visited nodes
        boolean[][] visited = new boolean[maze.length][maze[0].length];
        while (!queue.isEmpty()) {
            int size = queue.size();
            for (int j = 0; j < size; ++j) {
                int[] curr = queue.poll();
                maze[curr[0]][curr[1]] = '+';
                for (int i = 0; i < 4; ++i) {
                    int nx = curr[0]+directions[i];
                    int ny = curr[1]+directions[i+1];
                    if (nx < 0 || nx >= maze.length || ny < 0 || ny >= maze[0].length || maze[nx][ny] == '+' || visited[nx][ny]) {
                        continue;
                    }
                    if (nx == 0 || ny == 0 || nx == maze.length-1 || ny == maze[0].length-1) {
                        return steps_num+1;
                    } else {
                        visited[nx][ny] = true;
                        queue.offer(new int[] {nx, ny});
                    }
                }   
            }
            steps_num++;
        }
        return -1;
    }
    
}
``````

The third problem does not have any model algorithm to be solved. It need to discuss two possible situations: The number of question marks is odd or even?

1. Odd: Then Alice will always win the game.
2. Even: We only need to solve the unilateral case. If the difference of two parts is the multiples of 9.



## Weekly contest 249

The problem two is to find the number of substrings, which satisfy the rules below:

1. The substrings are palindromes.
2. The length is 3.

Just need to store the fisrt and last index of each characters appears in the string, and use a 2D vector to record the appearance of the middle character.

For example, if **bab** appears in the string, then store\[1\]\[0\] will be true.