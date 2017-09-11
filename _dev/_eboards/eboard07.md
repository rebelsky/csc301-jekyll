---
title: Eboard 07  The Master Theorem
number: 07
section: eboards
held: 2017-09-08
---
CSC 301.01, Class 07:  The Master Theorem
=========================================

_Overview_

* Preliminaries
    * Notes and news
    * Upcoming work
    * Extra credit
    * Friday PSA
    * Questions
* Detour - Recursion vs. iteration
* Recursion trees, revisited
* Proving asymptotic bounds of recursive functions
* The master theorem

### News / Etc.

* We are now 1/7 of the way through CSC 301.  After today's class, we'll
  be 1/6 of the way through CSC 301.
* I hope to get homework back to you on Monday.  (Probably only one of
  the two, but we'll see.)

### Upcoming work

* Reading for Monday: Review the Master theorem in CLRS 4.
* [Assignment 3](../assignments/assignment03), due 10:30 pm next Wednesday

### Extra credit (Academic)

* CS Table, Tuesday, Machine Ethics

### Extra credit (Peer)

* Sign up for CS picnic (but only if you plan to attend).
  (You can reflect on the sign-up process or on the picnic itself.)

### Extra Credit (Misc)

* Host a prospective student [ohc]

### Other good things

* Women's Tennis vs. Coe, TODAY at 4:30 p.m., High School
* Women's Tennis vs. Lake Forest, Saturday at 9 am High School
* Women's Tennis vs. Beloit, Saturday at 3 pm High School
* Les Duke Cross Country Meet, Saturday at 9 a.m., Country Club
* Men's Soccer vs. North Central College, Saturday at 1:00 p.m., Springer Field
* Women's Soccer vs. University of Wisconsin-Oshkosh, Sunday at 1:00 p.m., Springer Field

### Friday PSA

* You're great people.
* Please stay that way.

### Questions

On assignment 3, we have code and written.
 : Email Sam tarball of code.
 : Put written under Sam's door (or in the envelope, if he ever puts
   one out)

Recursion trees, revisited
--------------------------

* Drawing trees can help us estimate the running time!
* We show the size of the problem at each level.
* We can sum across each level to see the work at that level.
* We then sum those sums to get an overall estimate of the running time.
* This analysis requires that we identify the sum of the values at each
  level and the number of levels.
* On Wednesday, we built the recursion tree for `T(n) = 2*T(n/2) + cn`.

Exercises

* Build the recursion tree for `T(n) = 2*T(n/2) + c`.
* Build the recursion tree for `T(n) = 2*T(n/2) + n^2`.
* Build the recursion tree for `T(n) = 3*T(n/2) + c`.

Detour: Recursion vs. iteration
-------------------------------

Solving recurrence relations with the Master Theorem
----------------------------------------------------

The master theorem works for recurrences of the form
`T(n) = aT(n/b)+f(n)` or `T(n) <= aT(n/b)+f(n)` 

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
