---
title: Eboard 16  Sorting
number: 16
section: eboards
held: 2017-09-29
---
CSC 301.01, Class 16:  Sorting
==============================

_Overview_

* Preliminaries
    * Notes and news
    * Upcoming work
    * Extra credit
    * Questions
* Deletion in 2-3 trees
* Common sorting algorithms
* Characteristics of sorting algorithms
* Detour - Thinking about algorithm design
* Lower bounds on sorting algorithms

### News / Etc.

* Yes, I do intend to return exam 1 on Monday.  We'll discuss the exam
  on Monday in any case
* I was sorry to see so few of you at convocation yesterday.

### Upcoming work

* [Assignment 5](../assignments/assignment05) due next Wednesday at 10:30 p.m.

### Extra credit (Academic)

* Any of the Grinnell Prize events
* CS Table, Tuesday: Tapia
* CS Extras, Thursday: Grad school

### Extra credit (Peer)

### Extra Credit (Misc)

### Other good things

* Women's tennis Sunday at noon at high school
* Volleyball next Tuesday
* Take care of yourselves this weekend

### Questions

Deletion in 2-3 trees
---------------------

Useful things to get started.

1. Think about deletion at leaves.

2. It's useful to identify different situations.

3. Pay attention to the parent.

What cases do you come up with?  (You don't have to solve all of them,
just try to enumerate.)

* Singleton leaf - Can't just delete because how you fix depends
  on both parents and siblings.  (We will have to do some fix-up at
  the parent level before we recurse up the tree.)
* Pair leaf - Just remove one part.  (Unfortunately, this gets more complex
  as we move up the tree.)

Generalize for leaves

* Singleton leaf, singleton parent, singleton sibling
* Singleton leaf, singleton parent, pair sibling
* Singleton leaf, pair parent, all siblings singleton
* Singleton leaf, pair parent, all siblings pairs
* Singleton leaf, pair parent, one sibling singleton, one sibling pair
* When we do interior nodes, we will also have pair node.

Common sorting algorithms
-------------------------

Typically covered in 207

* Bubble
* Insertion
* Selection
* Quicksort
* Merge sort - recursive
* Merge sort - iterative
* Heap sort

Have heard of

* Radix
* Tom

Unreasonable

* Random permutation 
* Bogo
* Quantum bogo

Characteristics of sorting algorithms
-------------------------------------

_In choosing which sorting algorithm to use, what questions do I ask?_

* List or array?
* Do I need my sort to be stable?  "Identical" elements preserve order
* How big is the input?
* Input already mostly ordered?
* Cost/availability of extra memory?
* What resources do I prioritize?
* Who maintains my code?
* What operations are available to me?
* (Cost of those operations?  E.g., how expensive is a write?)
* What kind of data do I have?

Characteristics of primary algorithms (time, space, stable)

* Bubble
* Insertion
* Selection
* Quicksort
* Merge sort - recursive
* Merge sort - iterative
* Heap sort

Detour - Thinking about algorithm design
----------------------------------------

Lower bounds on sorting algorithms
----------------------------------

