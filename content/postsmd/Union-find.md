---
nr: 2
theme: ["all", "graph", "data-structures"]
id: Union-find
title: Union Find
image: \pictures\Union-find\maxresdefault.jpg
description: A union-find structure maintains a collection of sets. The sets are disjoint, so no element belongs to more than one set.
created: "2022-03-31"
updated: "2022-04-03"
author: Theodor Beskow
---
 
# Union Find
 
## What is Union Find?
 
A Union Find structure or a Disjoint-set data structure as it's also called is a common and useful data structure. The Union Find structure remembers what elements in a list are connected. You can also check how big the structures are, connect two structures and more. But unlike many structures like queue or a list, the Union Find structure you will have to code yourself. This is because you will often want to tweek the structure to fit the problem you are trying to solve. Union Find is also very fast with the find and unite funktion running in O(log n) time complexity.
 
<br>
 
## How to implement Union Find
 
A Union Find will almost always have to be implemented differently depending one what it is going to be used for. But even if two Union Finds are meant to do the same thing, they can still look vastly different. My Union Find usually look something like this in c++:
 
<br>
 
```cpp
 
struct Union_Find{
 
    int N;
    vector<int> p, siz;
    Union_Find(int N) : N(n){
        p.resize(N);
        siz.resize(N, 1);
        for(int i = 0; i < N; i++) p[i] = i;
    }
 
    bool same(int a, int b){
        return find(a) == find(b);
    }
 
    int find(int x){
        if(p[x] == x) return x;
        return p[x] = find(p[x]);
    }
 
    void unite(int a, int b){
        a = find(a);
        b = find(b);
        if(a == b) return;
        if(siz[a] < siz[b]) swap(a, b);
        p[b] = a;
        siz[a] += siz[b];
    }
};
```
 
<br>
 
The Union_Find function is called when creating the structure and is used to initialize it. In this case the structure uses arrays to remember how big the structures are with "siz" and what the representative are for every node with "p". The same function just returns true if a and b are in the same structure and if not the function returns false. The Unite function node a and node with each other. The Unite function does this by first getting the representative node for both a and b and then attaching them so that they both share the same representative node and update the size of the united set. The last function find returns the representative of the node x. But the function does not only find the representative of the node it also so all the visited nodes will be represented by the representing node directly and not create a long tree. This last find logic makes it so most of the structure's functions effectively run in O(log n) instead of O(n) which is a big difference. The image below shows how this find function compresses the amount of pointers you need to search through to get the representative of a node.
 
<br>
 
<img src="\pictures\Union-find\images.png" alt="find() img" style="width:80%; margin-left:10%;">
 
<br>
 
## Practical use
 
The Union Find structure is very useful in minimum or maximum spanning trees. In those problems a greedy solution is to always connect two nodes with the lowest cost granted they are not already connected. To do this you could use a Union find to keep trang on what nodes are connected. In <a href="https://open.kattis.com/problems/islandhopping" >this<SquareArrowUpRIght/></a> problem a Union Find could be used to keep track of the connected nodes.
 
<!--  <nuxt-link to="/about-us" class="linktext"> About us <SquareArrowUpRIght/></nuxt-link> -->
 
 
 
 

