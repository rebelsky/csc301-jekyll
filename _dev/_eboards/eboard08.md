---
title: Eboard 08  Roles of data structures and abstract data types
number: 8
section: eboards
held: 2017-09-11
---
CSC 301.01, Class 08:  Roles of data structures and abstract data types
=======================================================================

_Overview_

* Preliminaries
    * Notes and news
    * Upcoming work
    * Extra credit
    * Questions
* The master theorem
* Abstract data types
* Data structures
* A Dictionary ADT

### News / Etc.

* As the poet says, "The best-laid schemes o' mice an' men gang aft agley".
    * I did not get grading done this weekend.

### Upcoming work

* [Assignment 3](../assignments/assignment03), due 10:30 pm Wednesday
    * Code via email
    * Printed under door

### Extra credit (Academic)

* CS Table, Tuesday, Machine Ethics
* CS Extras, Thursday, Klinge Map Group on Cauldron

### Extra credit (Peer)

* Math/CS/Stats Picnic (sign up again)

### Extra Credit (Misc)

* Time Management Workshop, Tuesday, 11am, JRC 226.
* Host a prospective student [ohc]

### Other good things

* ???

### Questions

In doing the kth largest, do we make another array?
  : No.  That's inefficient.  Just keep track of the area that is of
    interest.
  : *Two* lb/ub: One for "This is the portion of interest", one for
    partitioning.

Should we use median of medians or kth largest or ...
  : I like randomized kth largest, but perhaps that's me.

Can we mutate the array?
  : Sure.  You can also create a copy (**once!**) and then mutate the 
    copy.

Can we just do the simple "median of an array of numbers" or should we
generalize?
  : It's C.  Generalizing is a pain.  Array of numbers is fine.

Should we submit our HackerRank code, too?
  : Yes.

Why doesn't HackerRank see my output?
  : You've probably forgotten to include a newline.

How should we organize our code for submitting.
  : kth-largest.c : Library that provides kthlargest procedure.
  : kth-largest.h : Corresponding header code
  : kth-largest-tests.c : Your test suite
  : kl.c : Command-line version (optional)
  : hr-median.c : The hackerrank code.
  : Makefile

If we work as a group on the code
  : Send me one code file.

The master theorem
------------------

Building recursion trees helped us understand a variety of different
recurrence relationships.

* If T(n) = 3*T(n/2) + c, then T(n) is in O(n^(log_2(3)))
* If T(n) = 2*T(n/2) + c, then T(n) is in O(n)
* If T(n) = 2*T(n/2) + n^2, then T(n) is in O(n^2)
* If T(n) = 2*T(n/2) + n, then T(n) is in O(n*logn)

Three issues:

* How much we divide the input for a recursive call
* How many recursive calls we make
* How much work we do in each call

There's probably a pattern.  

The master theorem works for recurrences of the form `T(n) =
aT(n/b)+f(n)` or `T(n) <= aT(n/b)+f(n)`.  These represent typical forms
of divide-and-conquer algorithms.

* What does `a` represent?
* What does `b` represent?
* What does `f(n)` represent?

There's a simpler version (which I'm taking from Weiss).  This is
for recurrences of the form `T(n) = aT(n/b) + O(n^k)`

1. If a > b^k, then T(n) is in O(n^(log_b(a)))

2. If a = b^k, then T(n) is in O((n^k)*log_2(n)))

3. If a < b^k, then T(n) is in O(n^k)

_I may need to recheck those._

We'll try some basic examples.

The more general computation depends on the relationship between _f(n)_ and
how quickly the `n/b` drops to 0.

1. If `f(n)` is in `O(n^(log_b(a)-e))` for some `e` > 0, then
  `T(n)` is in `Theta(n^(log_b(a)))`

2. If `f(n)` is in `Theta(n^log_b(a))`, then
  `T(n)` is in `Theta((n^(log_b(a))*log(n))`

3. If `f(n)` is in `Omega(n^(log_b(a)+e))`_ for some `e` > 0, and
  `af(n/b) <= cf(n)` for some `c` < 1 and large enough `n`, 
  then `T(n)` is in `Theta(f(n))`.



Abstract data types
-------------------

_Reflect on the following questions.  Be prepared to answer._

What is an abstract data type (ADT)?
  : An abstract way of holding data.  
  : Not a concrete implementation, but how do we use it and what
    do we use it for?
  : A list is a collection of values that we can dynamically extend
    (in restricted ways) and iterate.
  : A vector is a (mutable) collection of values that you can index.

Why do we use ADTs?
  : Helps us think about how we want to organize and access data
    depending on the situation.

How do you design ADTs?
  : Consider the overall *Philosophy*: How are you organizing the info?
    (I want to have a collection in which it is easy to add things and
    then see if I've added something.  We'll call that a "Set")
  : Consider the *Methods* that implement that philosophy.  `add` (core)
    `contains?` (core), `iterate` (optional), `remove` (optional/may
    separate us into two kinds of Sets)
  : Consider the *Use Cases* for that ADT.
  : Go on to the data structure


Data structures
---------------

_Reflect on the following questions.  Be prepared to answer._

What is a data structure?
  : Way of organizing (structuring) information (data) to achieve 
    some goal.
  
How do we use data structures?
  : To implement implement ADTs.
  : To support most algorithms.

How do you design/build data structures?
  : Overall *Approach* - Linked structure and array
  : *Details* of method implementations
  : *Running time* of method implementations

What relationship are there between ADTs and data structures?
  : data structures implement ADTs.
  : class vs. interface relationship in Java.
  : But ...

A Dictionary ADT
----------------

_Reflect on the following questions.  Be prepared to answer._

_If you haven't seen dictionaries before, think of them as a
generalization of hash tables._

What do you see as the primary *philosophy* of dictionaries?
  : A collection of values indexed by arbitrary key (e.g., a string)

What do you see as some natural *uses* of dictionaries?
  : A bunch of different lookup systems.
  : Implementing the values of variables in a dynamic programming 
    language

What do you see as the necessary *methods* a dictionary ADT should provide?
  : `put(key,value)`
  : `lookup(key)`
  : `replace(key,value)` - multiple philosophies
  : `remove(key)`
  
What do you see as *optional* methods a dictionary ADT might provide?
  : `iterate()` - what does this return?

Dictionary is another name for Map is another name for Dictionary is
another name for Table

What implementations of dictionaries do you know?
  : Hash tables
  : Assocation lists
  : Associative arrays
  : Sorted associative arrays
  : BSTs
  : Balanced BSTs
  : ...
