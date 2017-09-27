---
title: Eboard 14  2-3 trees
number: 14
section: eboards
held: 2017-09-25
---
CSC 301.01, Class 14:  2-3 trees
================================

_Overview_

* Preliminaries
    * Notes and news
    * Upcoming work
    * Extra credit
    * Questions
* Review: red-black trees
* 2-3 trees
* Insertion in 2-3 trees
* Deletion in 2-3 trees
* 2-3 trees vs. red-black trees
* B-trees

### News / Etc.

* I hope you had fun without me and enjoyed seeing a different model of teaching.
* I have not gotten grading done.  If there are particular things you think might
  be a problem, ask questions.

### Upcoming work

* [Exam 1](../exams/exam01) due Wednesday at 5:00 p.m.
* The next assignment will be distributed on Wednesday.

### Extra credit (Academic)

* CS Table, Tuesday: ???
* Google Stuff, Tuesday
* Convocation, Thursday

### Extra credit (Peer)

### Extra Credit (Misc)

### Good things to do

* GHS Homecoming Parade, Thursday, 4pm at or near GHS

### Questions

Will you accept mediocre formatting of our math?
  : Sure.

If I am breaking down summations (sum(sum(sum(...)))), should I explain
what rule I am applying for each summation?
  : Yes

The answers to sums a and b are standards.  Can I just cite them?
  : No.  Provide an anaysis of where the standard formula comes from

Do I have to prove my solutions to the recurrence relations using induction?
  : No.  Just show how you got it with some explanation.
  : There are three approaches, each gives enough info if you tell
    me what you are doing.

What do you want for code?
  : Print out of the important portions.
  : You can use a word processor or markdown or ...
  : I will not run the code; I can usually tell correctness by inspection.

Review: red-black trees
-----------------------

A red black tree is a binary search tree

* Properties mean that it is mostly balanced, height O(logn)
* Nodes are marked red or black.
* The black height of every leaf is the same (# of black nodes between
  root and leaf)
* Red nodes only have black children.
* Root is black.
* Leaves are black.
* The shortest path and the longest path can't be off by more than
  a factor of 2 (all black nodes vs. alternating red and black)

How do we maintain these properties when we insert or delete?

* We need to rotate things.  There are a lot of cases.
* Insert the node.  If the parent is black and the grandparent is black,
  you can just change the parent to red.
* See if we screwed up the height.  If so, rotate

We will come back to this.

2-3 trees
---------

* Balanced tree.
* Trinary: Nodes have two or three children and one or two values
* The three subtree are 
    * "less than first value"
    * "between first and second value"
    * "greater than second value"
* The height of every leaf is the same.
* The height must be logn or less.  We may, however, have to do two
  comparisons per node in searching, so the overall cost of find is
  O(2*logn), which is still O(logn)
* We'll make the leaves null wlog

Insertion in 2-3 trees
----------------------

You've reached the leaf.  You want to add another value.  What do you do?

* Easy case: The parent has only one value.  Just add a second value to
  the parent.
* Hard case: The parent has two values.  You can't just add a second value.
* Does it matter if you want to add to the left, middle, or right?  No.
* Option 1: If you have lots of two-value nodes, split them all up and
  reorganize.  Sam notes: Local and recurse is a good strategy.
* Option 2: Repeatedly move up?  But then you might hit the root.
* Think about what you could do locally and then move the problem up

Deletion in 2-3 trees
---------------------

2-3 trees vs. red-black trees
-----------------------------

B-trees
-------

