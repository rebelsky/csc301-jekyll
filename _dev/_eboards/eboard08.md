---
title: Eboard 08  Roles of data structures and abstract data types
number: 8
section: eboards
held: 2017-09-11
current: true
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

* ???

### Extra Credit (Misc)

* Time Management Workshop, Tuesday, 11am, JRC 226.
* Host a prospective student [ohc]

### Other good things

* ???

### Questions

The master theorem
------------------

Building recursion trees helped us understand a variety of different
recurrence relationships.

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
  `T(n)` is in `Theta(n^(log_b(a)*log(n)))`

3. If `f(n)` is in `Omega(n^(log_b(a)+e))`_ for some `e` > 0, and
  `af(n/b) <= cf(n)` for some `c` < 1 and large enough `n`, 
  then `T(n)` is in `Theta(f(n))`.

Abstract data types
-------------------

_Reflect on the following questions.  Be prepared to answer._

What is an abstract data type (ADT)?

Why do we use ADTs?

How do you design ADTs?

Data structures
---------------

_Reflect on the following questions.  Be prepared to answer._

What is a data structure?

How do we use data structures?

How do you design/build data structures?

What relationship are there between ADTs and data structures?

A Dictionary ADT
----------------

_Reflect on the following questions.  Be prepared to answer._

_If you haven't seen dictionaries before, think of them as a
generalization of hash tables._

What do you see as the primary *philosophy* of dictionaries?

What do you see as some natural *uses* of dictionaries?

What do you see as the necessary *methods* a dictionary ADT should provide?

What implementations of dictionaries do you know?

