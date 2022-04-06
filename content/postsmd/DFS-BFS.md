---
nr: 1
theme: ["all", "graph"]
id: DFS-BFS
title: DFS and BFS
image: "/pictures/DFS-BFS/grafo.jpg"
description: DFS and BFS are two different ways to search through a graph.
created: "2022-03-29"
updated: "2022-03-31"
author: Theodor Beskow
---
 
# DFS and BFS

## What is DFS and BFS?
 
DFS and BFS are two different ways to search through a graph. A DFS or depth first search searches as deep as possible first through one node before continuing to the next child. Compared to depth first search BFS or breadth first search searches all the neighbors of the currently visited nodes before searching deeper. These algorithms are very commonly used and easily implemented. Neither of the algorithms are able to handle weighted graphs. For weighted graphs you should instead use dijkstra or the bellman ford algorithm. The depth first search algorithm advantages is that it uses bit less time and space complexity than BFS. Breadth search first is a bit slower than the depth first search algorithm but BFS still has some use cases. BFS should be used when you for example want to find the shortest path between two nodes or if you want to detect if a graph is bipartite. The gif below shows the difference in what order DFS and BFS searches.  
<img src="\pictures\DFS-BFS\dfs-vs-bfs.gif" alt="DFS-BFS gif" style="width:100%;">
 
## How to implement DFS and BFS
 
There are multiple ways to implement a depth first search breadth first search. Both DFS and BFS in some way or another have to remember which nodes have already been visited. This can be done in many ways, but a solution that works in most cases and has a good time and space complexity is to have a list. I like to call this list seen but you can call it whatever you prefer. One advantage of the depth first search is that it is possible to implement it recursively. Recursion is when you call a function from within itself. This can be a bit mind bending for starters, but the technique is very useful and compact. You can see the recursive python solution down below:
 
```py
seen = [0] * n
def dfs_recursive(current_node):
    if seen[current_node]: return
    seen[current_node] = 1
 
    for neighbor in adj[current_node]:
        dfs_recursive(adj[current_node][neighbor])
 
dfs_recursive(start_node)
```
 
But if you want to use BFS, then you can't use this recursive solution. Instead, you will need to use the data structure queue. A queue does just what it sounds like, it places every new element in the back of the queue and takes out the old ones at the front. This method is similar to the recursive solution but with some modifications. Instead of a function we use a while loop checking if the queue is empty. We will also have to set the current_node to the top element of the queue and remove that element from the queue. In the rest of the algorithm the only difference is that instead of a function call we add that node to the queue. You can also use this technique when doing a DFS although you would have to change the queue to a stack. A BFS implementation using this technique in c++ could look something like this:
 
```cpp
vector<int> seen(n, 0);
queue<int> q;
q.push(1);
 
while(!queue.empty()){
    int current_node = q.front();
    q.pop();
    if (seen[current_node]) continue;
    seen[current_node] = 1;
 
    for(int neighbor = 0; neighbor < adj[current_node].size(); neighbor++){
        q.push(adj[current_node][neighbor]);
    }
}
```
 
## Practical use
 
Both DFS and BFS have their advantages and applications. DFS should be used if you for example want to detect bridges, detect loops or if the order in which you search through the graph is not important. In <a href="https://open.kattis.com/problems/countingstars" >this<SquareArrowUpRIght/></a> problem for example a DFS would fit perfectly to mark all the star pixels next to each other as the same star. Another example where DFS could be used is if you want to detect if there is a way from node a to node b. BFS is also very useful in many situations. Two such situations is if you want to find the shortest path in a graph or if you want to detect if a graph is bipartite. One problem when you could use a BFS is in <a href="https://po.kattis.com/problems/eldberget" >this<SquareArrowUpRIght/></a> problem. This is a bit more advanced BFS problem, although it is still a BFS problem. The difficulties in this one comes from you being able to walk over k flames and makes it so you have to pass another argument throgh the queue.
 
<!-- <br>
 
<nuxt-link to="/about-us" class="linktext"> About us <SquareArrowUpRIght/></nuxt-link> -->
 
 
 

