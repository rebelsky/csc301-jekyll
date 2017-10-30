---
title: Eboard 17  Lower bounds on sorting algorithms
number: 17
section: eboards
held: 2017-10-02
---
CSC 301.01, Class 17:  Lower bounds on sorting algorithms
=========================================================

_Overview_

* Preliminaries
    * Notes and news
    * Upcoming work
    * Extra credit
    * Questions
* Detour - Thinking about algorithm design
* Compare and swap algorithms
* Decision trees
* Estimating log(n!)

### News / Etc.

* I spent 20 hours grading this past weekend.  All of it went to CSC 151.
  I'm sorry.  Given how little time I have during the day on weekdays, it
  looks like I won't get exam 1 back to you until next Monday.
* I've therefore rearranged the schedule a bit.
* I brought you Star Wars fruit snax instead.

### Upcoming work

* [Assignment 5](../assignments/assignment05) due Wednesday at 10:30 p.m.

### Extra credit (Academic/Artistic)

* Any of the Grinnell Prize events
* CS Table, Tuesday: Tapia
* Cool talk Wednesday; Mary Beth Tinker
* CS Extras, Thursday: Grad school
* Nice Fish (play this weekend)
* Nice Fish talk Friday at 4ish

### Extra credit (Peer)

* Neverland players, performing stories by elementary school kids
  Thursday at 7, Friday at 7, Saturday at 2, Sunday at 7 in the Wall
  Theatre
* Mid-Autumn Festival Friday at 6:20 in Harris.  Free food!  (Which
  will disappear really quickly)

### Extra Credit (Misc)

### Other good things

* Volleyball vs. Knox Tuesday at 7:00 p.m.
* Men's Soccer Wednesday at 4:30 vs. Cornell
* Volleyball vs. Beloit, Friday at 7:00 p.m.
* Women's Tennis vs. St. Norbert, Saturday at 9:00 a.m.
* Volleyball vs. Lake Forest, Saturday at 1:00 p.m.
* Women's Tennis vs. Ripon, Saturday at 3:00 p.m.
* Football, Saturday at 1:00 p.m.

### Questions

Detour - Thinking about algorithm design
----------------------------------------

* First, design the algorithm using one of the techniques from day one
  or two of class.
    * Look for similar problems.
    * Use a common technique, such as greed or divide and conquer
    * "Work was really"
    * Try examples and then generalize
    * ...
* Try it on some reasonable inputs
* Next try to break it
* Next, try to prove it corrrect
* Analyze it for efficiency
* Can I do better?
* If you can't find a better solution ...
    * Live with it
    * Prove that it's the best possible.
    * (Find a proof)
    * Prove that it's as hard to solve as some other problem that has
      no better solution
    * Approximate
* Implement

Compare and swap algorithms
---------------------------

In most of the sorting algorithms we write, we ground sorting in
"compare and swap".  That is, compare two elements and switch them
if they are "out of order".

* Insertion stort
* Bubble sort
* Merge sort (well, maybe not, but it does rely on compare)
* Quicksort
* Selection sort
* Heap sort

Or perhaps "compare and do something or not"

The best of these is O(nlogn)

Can we do better?

No.

So we should prove that no sorting algorithm over arrays based on
comparisons of elements in the array can be better than O(nlogn).

Decision trees
--------------

We will model the algorithm as a tree.

* Nodes are questions (comparisons).
* Children are "do some work" then ask another question.
* Leaves are solutions.
* Since the tree models an algorithm, the shape of the tree depends
  only on the algorithm.  Some algorithms will keep it balanced
  some will be unbalanced.

Questions

* What is the shortest path from root to leaf in the tree for an input
  array of size n?
* How many leaves are in the tree for an input array of size n?
* (If time) what is the minimum possible height of this tree?

The shortest path possible from root to leave is n$a

Each path represents what the algorithm does on one permutation.  Each
permutation must have a different path.  n! leaves

If a binary tree with n! leaves (n!-1 internal nodes) is perfectly balanced,
its height is log_2(n!).

Hypothesis log_2(n!) is in Theta(nlog_2(n))

Ideas on approaching this:

* Constructive proof (find n0 and c)
* Use rules of logs and algebra.  
* Induction
* Intuition

Try breaking the problem into two parts and then using algebraic
manipulation.

log_2(n!) is in O(nlog_2(n))
log_2(n!) is in Omega(nlog_2(n))

What do you know about logs?

* 2^(log_2(n)) = n
* log(a*b) = log(a) + log(b)
* log(b^a) = alog(b)
* log(a/b) = log(a) - log(b)

log(n!) = log(n) + log(n-1) + log(n-2) + ... + log(1)

log(n!) < log(n) + log(n) + log(n) + ... + log(n) [because log(n-x) < log(n)]

log(n!) < nlog(n)

log(n!) = log(n) + log(n-1) + ... log(n/2) + log(n/2-1) + ... + log(1)

log(n!) > log(n) + log(n-1) + ... log(n/2) [we threw away non-zero terms]

log(n!) > log(n/2) + log(n/2) + ... log(n/2) [obvious]

log(n!) > n/2*log(n/2) 

log(n!) > n/2*(log(n) - 1) = n/2*log(n) - n/2

log(n!) is in Omega(nlogn)


Estimating log(n!)
------------------

Detour - Deletion in 2-3 trees
------------------------------

