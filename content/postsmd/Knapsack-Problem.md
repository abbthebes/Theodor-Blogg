---
nr: 3
theme: ["all", "dynamic-programming"]
id: Knapsack-Problem
title: Knapsack Problem
image: \pictures\Knapsack\1200px-Knapsack.svg.jpg
description: Description about me.
created: "2022-04-03"
updated: "2022-04-03"
author: Theodor Beskow
---

 
# Knapsack Problem
 
## What is the Knapsack Problem?
 
Knapsack refers to problems where a set of objects is given, and subsets with some properties have to be found. These objects could for example be different types of denominations or distances. The goal could be to find the least amount of demonations needed for a certain amount of money or is it possible to run exactly x meters with the available running tracks. Knapsack can often be solved by using dynamic programming.

<br>
 
## How to implement Knapsack

Because Knapsack problems are so different, there is not one solution that could solve all Knapsack problems. But the problems are still very similiar so the solution to a couple of ones will give you a general idea of to solve knapsack. Lets focus on the problem where we have the weighs [1,3,3,5] and we want to figure out the possible sums we can get to. It is possible to do this with a 2d array and going through one weight at a time we determain what sums are possible to get to with the previous possible sums and the the new weight. The code and array for this could look like this: 

<br>

```cpp
possible[0][0] = true;
for (int k = 1; k <= n; k++) {
    for (int x = 0; x <= W; x++) {
        if (x-w[k] >= 0) possible[x][k] |= possible[x-w[k]][k-1];
        possible[x][k] |= possible[x][k-1];
    }
}
```
<br>
<img src="\pictures\Knapsack\Capture.PNG" alt="find() img" style="width:80%; margin-left:10%;">
<br>

If you are confuser by the |= operator, it means or equals to. So possible[x][k] is true if it self is true or if the code of the right of |= is true. But there is a more neat solution to this problem that uses a bit less memory. 
 
## Practical use
 

 

