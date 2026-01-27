---
title: Insights for Problems
weight: 1
---


## Codeforces

### [Knight's Moves](https://codeforces.com/group/jtU6D2hVEi/contest/533280/problem/F)

Each move reduces manhattan distance to finish, so process dp in order of decreasing manhattan.

### [Anya and Cubes](https://codeforces.com/group/jtU6D2hVEi/contest/533251/problem/H)

Meet in the middle with 0/1/2 bitmask-style in $O(n^{3/2})$.

### [Lifeguards](https://codeforces.com/group/jtU6D2hVEi/contest/533251/problem/P)

Maintain a set of active lifeguards and linesweep.

### [Minimum Coverage](https://codeforces.com/group/jtU6D2hVEi/contest/533248/problem/G)

Linesweep and greedily take whatever ends the latest, while starting before the current segment ends.

### [Closest Cow Wins](https://codeforces.com/group/jtU6D2hVEi/contest/533249/problem/F)

Split into segments between enemy cows. Then it is always possible to place 1 or 2 cows to claim everything in an interval. Find for each interval, the maximum 1 cow and 2 cow patch scores. Add 2 cow score increase over 1 cow to list, along with 1 cows. Then each value in the array represents using one cow. Simply sort and take first n.

### [Alice and Apples](https://codeforces.com/group/jtU6D2hVEi/contest/533371/problem/G)

Sort into gaining and losing apples. Sort gaining by increasing $a$, and losing by decreasing $b$. We prove optimality with an exchange argument for two apples.

### [Elves and Reindeer](https://codeforces.com/group/jtU6D2hVEi/contest/533249/problem/G)

Hard. Binaryu search exchange 

### [Restructing Company](https://codeforces.com/group/jtU6D2hVEi/contest/533282/problem/G)

Since range unite is continuous, keep track of the last unmerged to the right for each index. Then if we have to range unite, just skip to next unmerged.

### [Remove the Ends](https://codeforces.com/contest/2064/problem/C)

Take prefix and suffix sums of positive and negative, because we will always take some prefix of positive from the left and some suffix of negative from the right (wipes it out kinda like swipe) so linear check for maximum.

### [Two Colors](https://codeforces.com/contest/2075/problem/C)

Loop over k, where the fence is painted 1 to k, k+1 to n. Subtract double counted colors that are sufficient to paint both ends.

### [Serval and MEX](https://codeforces.com/contest/2085/problem/B)

Split the array into two halves, MEX it if it has a zero. Then do a final combination.

### [Serval and the Formula](https://codeforces.com/contest/2085/problem/C)

Note any power of 2 does not share any set bits with a number less than it.



## DMOJ


### [Guessing Grades](https://dmoj.ca/problem/daacc1p5)
Key is to make the greedy filling independent of each choice.


### [Good Triplets](https://dmoj.ca/problem/ccc22s4)  

For each point, let c be the number of points that are on the next "half" of the circle. Then any triangle formed from these points will not include the origin. We can sum cases for 1/2/3 points from the current spot. These cases are independent and will not overcount as other starting points cannot possible include three points that are all not starting from that spot. However, we do doublecount the diameters, so if the circumference is even then we need to add back half the subtracted degenerate diameters.

### [Pick It](https://dmoj.ca/problem/pickit)  

Range dp, state is max score from l to r, for each balloon in l to r we take it as the last one to be popped. so then we can combine left and right for proper transition.

### [Balanced Trees](https://dmoj.ca/problem/ccc18s4) 

Math/skipping trick - write floor as an inequality statement, then rearrange to get range of i such that the subtrees are of weight v. The inequality also says i <= w//v, so the next i that changes the subtree weight should be w // v + 1.

### [Convex Hull](https://dmoj.ca/problem/ccc15s4)  

2D dijkstras, for each island keep minimum time, as well as minimum hull wear for that time

### [Ivana](https://dmoj.ca/problem/coci06c5p5)  

Circle = array * 2 + interval recursive dp, not too hard

### [Daily Commute](https://dmoj.ca/problem/ccc21s4)  

You always take the train for some prefix of your journey.

### [Swapping Seats](https://dmoj.ca/problem/ccc20s4)  

Another circle = array * 2, check every possible start point for section A, and realize that sorting A and B means C is done.

### [Palindromic Poster](https://dmoj.ca/problem/ccc23s3)  

%.

### [Matching Problem](https://dmoj.ca/problem/hkccc15s2)  

### [Swipe](https://dmoj.ca/problem/ccc24s3)

For each block of values in the target, get the source of the swipe.

### [Koala Balloons](https://dmoj.ca/problem/aac2p3)

Use PSA to check if blocked, as well as binary searching on maximum number of balloons.

### [Flowers DPQ](https://dmoj.ca/problem/dpq)

BIT to optimize transition to logn with 1. get maximum from 0 to h and 2. update maximum of height h (propogates to all higher heights)

### [An FFT Problem](https://dmoj.ca/problem/bts18p5)

DP in order of values to avoid overcounting, and process subset products backwards to avoid overwriting dp values.

### [King Gruff](https://dmoj.ca/problem/cco14p2)
For an edge, the shortest distance path through that edge is distA[u] + w + distB[v], where distA and distB are calculated with one run of dijkstra each from the start and end nodes. You can also create a super-source and super-sink, by connecting 0-weight edges from the source to any possible set of starting A's.

### [Exercise Deadlines](https://dmoj.ca/problem/cco20p2)
Process back to front and count inversions in nlogn with BIT. Key is to process right to left, because its most constrained: try to deal with most restrictive first.

### [Math Homework](https://dmoj.ca/problem/ccc21s5)
When there is a value in array that needs to satisfy many range constraints, try considering all combined constraints on one position rather than constraing by constraint. Also, when there are monotonic functions (gcd, and, or, min, max) that have a shrinking property on a range, there are usually far fewer state changes than there are elements in that range. You can track the indices where it actually changes and binary search or something.


## USACO

### [2D Conveyor Belt](https://usaco.org/index.php?page=viewproblem2&cpid=1448)

Offline processing key takeaways:
- When you are given all queries to start.
- When the problem involves an operation whose reverse operation is fast.
- Often removing something (ex. removing connections -> DSU for reverse is fast, min/max/gcd removal, reverse the order of processing)
- Another example is blocking cell, -> opening cell (bfs/flood fill)
- Deleting value -> inserting value (heap, set)

Key for this problem is a new conveyor belt might cut off a large portion, which requires recalculation. But opening a loop is just once dfs.

### [Cow Checkups](https://usaco.org/index.php?page=viewproblem2&cpid=1470)
Find a mathematical formula to calculate, then split the min(a, b) expression into cases when a is true and when b is true. Sum by maintaining a stack.
