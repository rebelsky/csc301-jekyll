---
title: Eboard 10  An introduction to trees
number: 10
section: eboards
held: 2017-09-15
---
CSC 301.01, Class 10:  An introduction to trees
===============================================

_Overview_

* Preliminaries
    * Notes and news
    * Upcoming work
    * Extra credit
    * Questions
* Hash tables: semi-formal analysis
* Other ways to represent dictionaries
* Trees

### News / Etc.

* Note: I expect that you follow GNU style guidelines when you submit
  C code to me.  If you don't know those guidelines, you can find them 
  on the Interweb.
* Note: You should be using gdb or lldb.  I do not want to see code with
  lots of `printf`s.  
    * Actually, I expect that you would *ever* use `printf` for 
      tracing output.  Use `fprintf (stderr, ...)`
* Cough drops

### Upcoming work

* Read Skiena Chapter 3 for Monday.
* [Assignment 4](../assignments/assignment04), due 10:30 p.m. Next Wednesday
    * Implement hash tables in Scheme.
    * Reflect on how to implement sets.

### Extra credit (Academic)

* CS Table, Tuesday, Hacktivism
* CS Extras, Thursday, Study abroad

### Extra credit (Peer)

* Elephantitus, this weekend. (Grinnell High School and Middle School)
    * High school: West on 8th
    * Middle school: South on East
* CS Picnic! 5pm today, Merrill park West.  (11th and Main)
* AppDev intro thingy Sunday at 1pm 3919.

### Extra Credit (Misc)

* Brazillian Jiu Jitsu Club, Saturday (2017-09-16) 5 PM to 6:30 PM in 
  the Bear Multipurpose Dance Studio

### Other good things

* Take care of yourselves and those around you.

### Friday PSA

* Don't feel pressure.  The choices you make can/should be your own.
* Consent is absolutely, positively, necessary.
* Embrace self-gov!

### Questions

Hash tables: semi-formal analysis
---------------------------------

A hash table is a data structure that implements dictionaries.

* We store key/value pairs in an array.
* To store a key/value pair, we compute a "hash" of the key (a function
  from the key to a number).  The key/value pair goes in that hash % 
  array size.
* To look up a value by key, we compute a "hash" of the key and look in
  the corresponding index (see previous step)
* Complexity: The pigeonhole principle suggests that multiple things will
  hash to the same array location, so we need to deal with conflicts
     * Option 1 ["Bucketed"/"Chained"]: Store a linked list of key/value
       pairs in each array entry
     * Option 2 (probed): Look at nearby cells.

Practice hash: Add up the first three letters in your first name

* a is 0, b is 1, c is 2, d is 3, e is 4
* f is 5, g is 6, h is 7, i is 8, j is 9 
* k is 10, l is 11, m is 12, n is 13, o is 14 
* p is 15, q is 16, r is 17, s is 18, t is 19 
* u is 20, v is 21, w is 22, x is 23, y is 24

Note: When the array gets more than 50% full (# of key/value pairs vs. 
capacity of array), we expand the array.

_We have said informally that hash tables have expected Theta(1) behavior._

_In this class, we are attempting more formal analyses.  So, how could you
predict how long it would take to add a key/value pair?_

_Hint: Consider what happens when we add an element to a 50% full probed
hash table with a relatively good hash function._

* 1/2 look at 1 cell    1/2
* 1/4 look at 2 cells   1/2
* 1/8 look at 3 cells   3/8
* 1/16 look at 4 cells  4/16 = 1/4
* 1/32 look at 5 cells  5/32

We could do some extra analysis to see that the sum is bounded by a
constant.  I"m too lazy.

Other ways to represent dictionaries
------------------------------------

_What are other ways you might represent a dictionary?  Try to come
up with at least two that you've seen already (one from CSC 151, one
from CSC 207) and one new one._

* In CSC 151, we learned about association lists, lists of key/value 
  pairs.
    * O(n) add, O(n) to find
* In CSC 207, you learned about binary search trees
    * Binary tree with key/value pair at each node
    * Things to the left have smaller keys
    * Things to the right have larger keys
    * O(depth) to add or find
    * O(n) to add or find unless you are sure that the tree is balanced.
* In CSC 207, you learned about balanced binary trees (red/black trees)a
    * O(logn) to add or find
    * Complicated
    * We will cover them in 301
* In CSC 207, we learned about tries, O(keylength)
    * We will consider those in 301
* Vector key/value pairs (Associative Array)
    * add is probably O(n)
    * find is probably O(n)
* Sorted array
    * add is O(n)
    * find is O(logn)
