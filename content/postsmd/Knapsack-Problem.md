---
nr: 3
theme: ["all", "dynamic-programming"]
id: Knapsack-Problem
title: Knapsack Problem
image: \pictures\Knapsack\1200px-Knapsack.svg.jpg
description: Knapsack problems have objects given, and properties have to be found.
created: "2022-04-03"
updated: "2022-04-09"
author: Theodor Beskow
---
 
 
# Knapsack Problem
 
## What is the Knapsack Problem?
 
Knapsack refers to problems where a set of objects is given, and subsets with some properties have to be found. These objects could for example be different types of denominations or distances. The goal could be to find the least amount of denominations needed for a certain amount of money or is it possible to run exactly x meters with the available running tracks. Knapsack can often be solved by using dynamic programming.
 
<br>
 
## How to implement Knapsack
 
Because Knapsack problems are so different, there is not one solution that could solve all Knapsack problems. But the problems are still very similar so the solution to a couple of ones will give you a general idea of how to solve knapsack. Let's focus on the problem where we have the weights [1,3,3,5] and we want to figure out the possible sums we can get to. It is possible to do this with a 2d array and going through one weight at a time we determine what sums are possible to get to with the previous possible sums and the new weight. The code and array for this could look like this:
 
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
 
If you are confused by the x |= y operation, it means x = x | y. The |(or) operator actually looks at the bits and the bit is a one if it's a one in x or y. But in this case we don't have to worry about any of this because x and y are booleans. Therefore x is true if x or y is true. So possible[x][k] is true if it self is true or if the code of the right of |= is true. But there is a more neat solution to this problem that uses linear memory instead of squared with the amount of weights and maximum sum.
 
```cpp
possible[0] = true;
for (int k = 1; k <= n; k++) {
    for (int x = W; x >= 0; x--) {
        if (possible[x]) possible[x+w[k]] = true;
    }
}
```
Now the time complexity is the exact same but the space complexity is much better because we calculate all the possibilities all in the same row instead of a new one for every weight.
 
## Practical use
 
Knapsack is good if you want to choose elements optimally. A good and often used example of Knapsack is having different money bills and wanting to get to a set sum with as few as possible. A challenging knapsack problem is <a href="https://po.kattis.com/problems/springoalla" >this<SquareArrowUpRIght/></a>. If you want a tip for solving this problem is adding your own distances of first running the full distance and then running the half distance for the cost of two runs. We only couple one half distance in the new distance because it is never advantageous to run multiple half distances.
 
 
 

