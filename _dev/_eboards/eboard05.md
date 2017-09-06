---
title: Eboard 05  Divide-and-conquer algorithms and structures
number: 05
section: eboards
held: 2017-09-04
---
CSC 301.01, Class 05:  Divide-and-conquer algorithms and structures
===================================================================

_Overview_

* Preliminaries
    * Notes and news
    * Upcoming work
    * Extra credit
    * Questions
* Quick followup on asymptotic analysis
* Divide and conquer, in theory
* Review of divide-and-conquer algorithms and structures
* Finding the median value in an array
* Exponentiation with integer exponents
* Analyzing divide-and-conquer algorithms

### News / Etc.

* Happy Labor day.
* The Web site is still under development.  Let me know about broken
  links and such.  (But please do try reloading the page.)
* Piazza is useful.

### Upcoming work

* [Assignment 2](../assignments/assignment02), due 10:30 pm Wednesday.

### Extra credit (Academic)

* Rosenfield symposium, this week.  (Lots of different events)
* CS Table on Doxxing.

### Extra credit (Peer)

* Coffee Hour with German House, Tuesday, Above the Grill, 4:15 pm

### Extra Credit (Misc)

* Community Hour (Dialogues Across Difference), Tuesday at 11 a.m. in JRC 209.
* CLS Kick-Off Event, Tuesday at 11 a.m. in "North Campus Grove".
* Host a Prospie!

### Good things, no extra credit

### Questions

Quick followup on asymptotic analysis
-------------------------------------

We have a formal definition of big-O and an informal understanding of
what the parts of the definition represent.  What changes about the
definition when we do Big-Theta and Big-Omega.

* How does the big O definition change for Theta(n) or Omega(n)
* Yay!  The folks called on seem fairly confident.

How do you figure out the big-O (or other) bound on an algorithm?

* For an iterative algorithm, you count the loops.
* For a recursive algorithm, think about it.

Sample iterative algorithm

```
i = n
while (i > 1)
  for (j = 0; j < i; j++)
    some-constant-time-operation
  end for
  i = i/2;
end while
```

* The outer loop runs log_2(n)-ish.
* The inner loop runs O(n)-ish, at worst.
* So, we multiply the two and say this is an O(nlogn) algorithm.

Is there a tighter bound?

* n + n/2 + n/4 + ... + 1
* n 
* n + n/2 = 3/2 n
* n + n/2 + n/4 = 7/4 n
* n + n/2 + n/4 + n/8 = 15/8 n
* < 2*n
* O(n)

Moral: We may have to think more carefully about how the loops are interacting.

Another approach: Run the program on lots of data points and interpolate
the graph.

Divide and conquer, in theory
-----------------------------

An approach to algorithm design that involves splitting the input in half,
solving the problem (perhaps modified slightly) on one or both halves,
and then combining those solutions into a solution to the overall problem.

* Example: Find Occifer Motta

Review of divide-and-conquer algorithms and structures
------------------------------------------------------

What are some algorithms and data structures that you have encountered that
involve divide and conquer?

* Trees - Divide and conquer data structure (heaps, binary search trees)
* Binary search
* Quicksort
* Merge sort

The divide should be reasonably good for the behavior we want from
divide-and-conquer algorithms.  For example, Quicksort works poorly
if the pivot is always the second-largest value.

Complexities:

* Choosing what to divide.
* Choosng how to divide.

Finding the median value in an array of values
----------------------------------------------

Given an unsorted array, [a1 ... an], where n is odd and no two values
are the same, find the value a such that (n-1)/2 elements are smaller
than a and (n-1)/2 elements are larger.  You may not sort the array, but
you may rearrange the values.

### Idea zero: Ignore the requirements

1. Sort
2. Look in the middle

### Idea one: Just plow ahead

1. Find the median of the left half (not including the middle element?)
2. Find the median of the right half (not including the middle element?)
3. Do something with those two medians

Example input: 1,10,100,1000,2,20,200

### Idea two: Change the problem slightly - Put the median in the middle.

1. Pick a pivot randomly from the elements of the array
2. Rearrange the elements so that everything less than the pivot is 
left of the pivot, everything greater than the pivot is to the right.
3. Repeat on the subarray.

* n steps to partition the first time
* n/2 steps to partition the second time
* ...

### Idea three: Change the problem significantly - Find the kth largest
element in an arbitrary subarray.

Exponentiation with integer exponents
-------------------------------------

In a language that provides arbitrary precision numbers, compute x^n for
non-negative integer n.

* If n is even, x^n = square(x^(n/2))
* If n is odd, x^n = x*(square(x^((n-1)/2)))

Analyzing divide-and-conquer algorithms
---------------------------------------

*On Wednesday.*
