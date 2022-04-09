---
nr: 4
theme: ["all", "dynamic-programming"]
id: Sliding-Window
title: Sliding Window
image: \pictures\Sliding-Window\h3h2h4s11pjgla88pqzp.jpg
description: Description about me.
created: "2022-04-08"
updated: "2022-04-09"
author: Theodor Beskow
---

 
# Sliding Window
 
## What is a Sliding Window?
 
A sliding window is a way to search trough a array. Sliding window will be able to find a "window" in the array with a seratain property that you want. With a window meaning all elements between one start point and one end point in the array. There could for example be no restriction at all, a certain maximum amount of elements, or a max summed weight. 
 
## How to implement Sliding Window

The sliding window will have to be modified depending on the type of sliding window you are writing. But all sliding window are pritty similar. This is an example of a sliding window when we want to find the maximum sum of five consecetive elements: 
```cpp
for (let i = 1; i <= arr.length - 5; i++) {
    currSum -= arr[i - 1]; 
    currSum += arr[i + 4]; 
    largestSum = max(largestSum, currSum);
}
```

But all sliding windows are not this simple. If you for example want to long a consecetive row of elements could be with a restriction of a sertain maximum weight, the sliding window cloud look like this:

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
 
## Practical use
 

 



