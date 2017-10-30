---
title: Eboard 18  O(n) sorting algorithms
number: 18
section: eboards
held: 2017-10-04
---
CSC 301.01, Class 18:  O(n) sorting algorithms
==============================================

_Overview_

* Preliminaries
    * Notes and news
    * Upcoming work
    * Extra credit
    * Questions
* A sorting exercise
* Other strategies for sorting
* Bucket sort
* Radix sort

### News / Etc.

### Upcoming work

* [Assignment 5](../assignments/assignment05) due tonight at 10:30 p.m.
* [Assignment 6](../assignments/assignment06) due Wednesday after
  break at 10:30 p.m.

### Extra credit (Academic)

* Cool talk Wednesday; Mary Beth Tinker
* CS Extras, Thursday: Grad school

### Extra credit (Peer)

* Neverland players.
* RTS Friday in Loose Lounge at 9:30 p.m.
* Saturday 1-3 p.m. art thingy in Bucksbaum Rotunda

### Extra Credit (Misc)

* Thursday night movie.

### Other good things

* Volleyball vs. Beloit, Friday at 7:00 p.m.
* Women's Tennis vs. St. Norbert, Saturday at 9:00 a.m.
* Volleyball vs. Lake Forest, Saturday at 1:00 p.m.
* Women's Tennis vs. Ripon, Saturday at 3:00 p.m.
* Football, Saturday at 1:00 p.m.

### Questions

Yay?
  : Yay!


A sorting exercise
------------------

* You have a stack of cards.  Each letter of the alphabet appears once.
  What do you do?
* You have a much larger stack of cards.  Each letter of the alphabet 
  appears many times (not all the same).  What do you do?
  What do you do?

Idea 1: Somewhat parallel merge sort.  Divide the cards between the members
of the group.  Tell them to sort (presumably using regular merge sort)
then merge them all together.  4th place

Idea 2: Spread them out and do selection sort, but with faster selection
because you can look at everything at the same time.  (Won't scale, not
really computational.)  3rd place

Idea 3: Put them in twenty six buckets and then pick up the buckets.
O(n+m), where n is the number of elements and m is the number of buckets.
2nd place.

Idea 4: Divide and conquer using the binary representation.  One bucket
for things with 0's on the left, one bucket for things with 1's on the
left.  (And then sort each.) last place

Idea 5: Insertion sort.  Won by cheating.

Other strategies for sorting
----------------------------

O(nlogn) algorithms we did not know what the data were.  Here, we know
what kind of data we have and the bounds.

Suppose the bounds are big.  E.g., the data are all integers.  We can't
use the standard bucket sort, but perhaps others.

Our lower bound proof was based on compare and swap.  It doesn't apply
to bucket sort.

Bucket sort
-----------

You figured it out.  Make buckets.  Put things in buckets.  Maybe recurse.
Put it all back together.

Radix sort
----------

Assume you have a fixed-length binary representation.  Split things by
leftmost bit.  Put them back together.  Split by next bit.  Put them
back together. ...
