---
title: Insights for Problems
weight: 1
---

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


---


### [Guessing Grades](https://dmoj.ca/problem/daacc1p5)
asd


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



