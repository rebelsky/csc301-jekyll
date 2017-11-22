---
title: Eboard 35  Dynamic programming (2)
number: 35
section: eboards
held: 2017-11-20
---
CSC 301.01, Class 35:  Dynamic programming (2)
==============================================

_Overview_

* Preliminaries
    * Notes and news
    * Upcoming work
    * Extra credit
    * Questions
* The stamps problem, concluded
* General strategies for dynamic programming
* The knapsack problem

### News / Etc.

* Exam 2 returned.  We'll discuss it on Wednesday.
    * Please submit your epilogue if you have not done so already.
    * Lots of issues on problem 2.
* I hope to return exam 1 on Wednesday.
* "There's not a lot of time, how will I improve my grade if I'm not
  doing as well as I think I should be."
    * We'll figure something out.

### Upcoming work

* [Assignment 9](../assignments/assignment09) distributed.

### Extra Credit (Academic/Artistic)

* Community hour panel on gun regulations, tomorrow.
* CS table on "the gig economy" tomorrow.

### Extra credit (Peer)

### Extra Credit (Misc)

### Other good things

* Harp concert Tuesday night.

### Questions

The stamps problem, concluded
-----------------------------

Goal: Given a set of stamp prices, and a desired price, find the minimum
number of stamps to make that price.  

Example: [1,2,5,7,15,25]

Tried: 23, 21, 37

Greed fails for 21 and 37

The only strategy that seems to work is exhaustive search.

* Good: Correct
* Bad: Inefficient

When you are faced with this situation, you can

* Try to fix the algorithm
* Try to come up with a new algorithm
* Relax your constraints - I'm okay if the algorithm comes up with a
  value that is no more than twice the minimum number of stamps.
* Try a probabilistic approach

Sam has been teaching 151.  Student, in finding the largest element in
a list, often write something like the following.

```
;;; Precondition:
;;;   lst is nonempty
(define largest
  (lambda (lst)
    (cond
      [(null? (cdr lst))
       (car lst)]
      [(> (car lst) (largest (cdr lst)))
       (car lst)]
      [else
       (largest (cdr lst))])))
```

This seems correct, but it can be *slow* because we potentially do 
two recursive calls.  In fact, in each recursive call, we may be doing
two recursive calls.  This is exponential when the list is in order
from smallest to largest.

Getting around this

* a: Keep track of the largest so far.
* b: Divide and conquer
* c: When you see two identical expressions (in any language), we can
  name the result of those two expressions.

```
(define largest
  (lambda (lst)
    (cond
      [(null? (cdr lst))
       (car lst)]
      [else
       (let ([largest-in-cdr (largest (cdr lst))])
         (if (> (car lst) largest-in-cdr)
             (car lst)
             largest-in-cdr))])))
```

This small change has taken an exponential algorithm and made it linear.

We will try something similar with the stamps problem.  Observation:
If we've computed the minimum stamps for 35 cents once, we don't need
to compute it a second time.

How do we avoid computing it a second time?  Use a table to store the
things we've computed.  

* Initialize the table with "unknown"
* When you call minstamps(val), look in the table for val.  
* If it's there, just return the value in the table.
* If not, do the full computation, update the table, and return the
  computed value.

This strategy, which I tend to call "caching" can be useful for a wide
variety of problems.  If a procedure is "pure" (side-effect free, always
returns the same output given the same input), we can cache it.

It is rare that it is implemented explicitly in a programming language,
so we can implement it ourselves.

Our "exhaustive search" has become linear in the size of the problem.

We can now make things better by rethinking how we compute the table.

We can compute starting with 1 or 0, and go up to the number of stamps.

General concepts
----------------

When you are faced with a recursive exhaustive search solution.

* Make a table of solutions.
* Build that table from small to large.

The knapsack problem
--------------------

You can carry a fixed weight in your knapsack.

You have a bunch of (weight/value) pairs.

Your goal: Maximize the value you can put in your knapsack and keep it
within the desired weight.

Like the stamps problem, except:

* Maximize, rather than minimize
* Not all items are created equal
* Finite number of each item (assume 1)

All weights and values are positive.

Question 1: How might you solve this using dynamic programming?

Question 2: Why doesn't greed work for this problem?

An example: Capacity is 10

```
weight  value   ratio
10      10      1
 2       4      2
 2       3      1.5
 2       3      1.5
 2       3      1.5
 3       4      1.33...
 3       4      1.33...
```

Greed: Take heaviest: Fails.

Greed: Take best value/weight ratio.

* 2,4
* 2,3
* 2,3
* 2,3
* Value of 13

Better solution

* 2,4
* 2,3
* 3,4
* 3,4
* Value of 15

Caching will be a bit harder here.  Think about how to do it over the
next day and 23 hours.
