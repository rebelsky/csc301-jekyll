---
title: 'Assignment 1: Getting Started'
link: true
assigned: 2017-08-25
due: 2017-08-30
due-time: 10:30pm
---
# {{ page.title }}

*Due:* {{ page.due | date: '%A, %-d %B %Y' }} by {{ page.due-time }}

*Summary*: In this assignment, you will practice designing and
implementing structures and algorithms.

*Purposes*: To help you think about the relationship between the ways
we describe structures and algorithms abstractly and the details 
necessary when we implement them.  To help you recall some of the
things you learned (or might have learned) in prior courses.

*Collaboration*: You may discuss this assignment with anyone you like,
provided you credit such discussion when you submit the assignment.
You will learn more if you do most of the coding on your own, but you
may choose to submit the code for the assignment as a pair or trio.

*Submitting*: Create a tarball from your code and then mail it to your
course instructor with a subject of **CSC 301 Assignment 1 (Your Name)**.
You should, of course, substitute your name in that subject.

*Warning*: So that this assignment is a learnign experience for everyone,
we may spend class time publicly critiquing your work.

*Evaluation*: We will primarily evaluate your work on its *correctness*
(e.g., does it compute what it is supposed to; does it meet the
requirements of the assignment); *clarity* (e.g., is the code easy to
read, is it well formatted and documented); and *efficiency* (e.g., does
it achieve its goal quickly and with limited resources).

## Problem 1: Heaps

In CSC 207, you learned about heaps as an implementation of priority
queues.  If you need a refresher, CLRS provide an in-depth explanation
of heaps in Chapter 6.

Implement arbitrary-sized heaps in Scheme.  You should store the values
in a vector.  When the vector fills, you should build a new, larger,
vector and copy the values to that vector.  I would recommend that you
implement heaps as three-element vectors, one of which holds the size
of the heap (not the capacity), one of which holds the vector that
represents the elements of the heap, and one of which hold the comparator
used to determine priority.

```
;;; Procedure:
;;;   heap-new
;;; Parameters:
;;;   higher-priority?, a binary predicate
;;; Purpose:
;;;   Create a new heap.
;;; Produces:
;;;   heap, a heap
(define heap-new
  (lambda (higher-priority?)
    (vector 0 (make-vector 31) higher-priority?)))
```

In the code above, the 0 represents the initial size of the heap and
the 31 represents the initial capacity.

Note that `(higher-priority? a b)` is supposed to return true when
`a` is higher priority than `b` and false otherwise.

You should implement the following procedures

* `(first heap)`, which returns the highest-priority element in the heap;
* `(get heap)`, which returns and removes the highest-priority element
  in the heap; and
* `(add heap value)`, which adds a value to the heap.

## Problem 2: Robotic Motion

In section 1.1, Skiena describes a series of heuristics for choosing
an order of points to solder so as to minimize total distance traveled.

Using a language of your choice, implement four heuristics (procedures)
that take a sequence of points as input and produce an order in which
to solder the points.

1. One that starts at a random point and uses the "closest point next"
strategy.

2. One that does a diagonal sweep from the top-left corner to the
bottom-right corner.  If two elements are on the same diagonal, visit
the leftmost one first.

3. One that selects the points in random order.

4. One of your own design.

Finally, Then write a program that generates at least ten different random
sets of points and determines the total distance traveled for that
set of points for each of the four heuristics.
