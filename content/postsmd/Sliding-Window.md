---
nr: 4
theme: ["all", "dynamic-programming"]
id: Sliding-Window
title: Sliding Window
image: \pictures\Sliding-Window\h3h2h4s11pjgla88pqzp.jpg
description: A sliding window is a way to search through an array.
created: "2022-04-08"
updated: "2022-04-16"
author: Theodor Beskow
---
 
 
# Sliding Window
 
## What is a Sliding Window?
 
A sliding window is a way to search through an array. Sliding windows will be able to find a "window" in the array with a certain property that you want. With a window meaning all elements between one start point and one endpoint in the array. There could for example be no restriction at all, a certain maximum amount of elements, or a max summed weight.
 
## How to implement Sliding Window
 
The sliding window will have to be modified depending on the type of sliding window you are writing. But all the sliding windows are pretty similar. This is an example of a sliding window when we want to find the maximum sum of five consecutive elements in javascript:
```js
for (let i = 1; i <= arr.length - 5; i++) {
    currSum -= arr[i - 1];
    currSum += arr[i + 4];
    largestSum = Math.max(largestSum, currSum);
  }
```
 
But all sliding windows are not this simple. If you for example want the longest consecutive row of elements restriction with a certain maximum weight, the sliding window could look like this in c++:
 
```cpp
int ans = 0;
ll sum = v[0];
int l_point = 0;
int r_point = 0;
while(r_point != v.size()){
    if(sum <= budget) {
        ans = max(ans, r_point-l_point+1);
        r_point++;
        if(r_point == v.size()) break;
        sum += v[r_point];
    }else{
        sum-=v[l_point];
        l_point++;
    }
}
```
 
<br>
 
<div class="flex flex-wrap">
    <div class="w-full md:w-1/3">
        These sliding windows are written in c++ and javascript but if you use another language like python you could probably still get the general idea of the solutions. The way sliding windows operate in linear time complexity instead of n^2 is that it searches a bit smarter. Instead of searching through all the already searched elements for every shift forward, you only check the elements that are actually changing. If this is still a bit confusing for you, here is a picture to visualize how the algorithm searches. The visualized difference between the sliding window and the n^2 is that in the n^2 the space in between these orange dots would also be filled.
    </div>
    <div class="w-full md:w-2/3">
        <br>
        <img src="\pictures\Sliding-Window\zsGl7.png" alt="sliding window img" style="width:80%; margin-left:10%;">
    </div>
</div>
 
<br>
 
## Practical use
 
Sliding wind is very useful when you for example want to find a subarray in an array with a certain property. An example when you could use this algorithm is if you want to find the longest beach length you could buy with a certain amount of money. This is exactly what you need to do in <a href="https://pofinal22.kattis.com/problems/pofinal22.badstrand" >this<SquareArrowUpRIght/></a> problem. You could solve this in n^2 time complexity by checking all possibilities but that's too slow. Instead you should do it in n time complexity by using a sliding window. If you have problems solving this problem I suggest looking at the second sliding window example in this blogpost.  
 
 
 
 
 
 
 
 
 

