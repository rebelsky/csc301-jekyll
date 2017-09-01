---
title: Eboard 02  Shortest path
number: 02
section: eboards
held: 2017-08-28
---
CSC 301.01, Class 02:  Shortest path
====================================

_Overview_

* Preliminaries
    * Notes and news
    * Upcoming work
    * Extra credit
    * Questions
* Formalizing the problem
* Selecting possible approaches
* Sample solutions
* Analyzing the sample solutions
* Hints
* A more common solution

### News / Etc.

* I will once again take quick attendance.
* Take a card!
* *Thank you!* to the students who started assignment 1 early and
  have been sending along questions.
* If you have not yet signed the department's academic honesty policy,
  please do so now.
* The Web site is still under development.  Expect some significant
  changes to the topics, but not to the timing of homework assignments
  and examinations.
* I will check in on daily note-taking responsibilities on Wednesday.
* We now have a Piazza site (thanks AV).
* Be responsible for your classroom.  Make sure that your work area is
  as good or better than you found it.  At the end of class
    * Pick up and discard your trash.
    * Return your playing card to me.
    * Push in your chair.
   
### Upcoming work

* [Assignment 1](../assignments/assignment01), due 10:30 pm Wednesday 

### Extra credit (Academic)

* Community time: Healing from Hate, Tuesday, 11am, JRC 101.
* CS Table, Tuesday noon, topic tbd, Whale room.
* CS Extras, Thursday 4:15pm, Contracts.  Snacks at 4pm.

### Extra credit (Peer)

* Try out for Neverland players, today at 4:30 p.m. in The Wall (one of
  our two black-box theatres).
  (Act out stories written by middle-school students.)

### Good things to do

* Ag days Thursday.

### Questions

Can you fix the link to the eboard?
  : Tonight, I hope

Are the points in two-space?
  : Yes.

What is a diagonal sweep?
  : Top left to bottom right.  Kinda like horizontal, but 45 degrees off.

Can we do something utterly stupid for 2d, or would you like us to have
a rationale for our heuristic?
  : Some rationale would be nice, but something stupid is also okay if
    you can't come up with a good rationale.

What should `add` return?
  : Option 1: Nothing
  : Option 2: The modified heap

Shouldn't it be called `add!`?
  : Yes.

How do we change the size of the heap?
  : `(vector-set! heap 0 (+ 1 (vector-ref heap  0)))`

What happens when we want to grow the size of the underlying vector of
elements?
  : You should be able to do something similar at position 1.

Can we work with others?
  : Yes.

How do I compare the priority of two elements in a vector?
  : `(if (higher-priority? (vector-ref vec i) (vector-ref vec j)) ...)`
  : This assumes you've written something like 
    `(let ([higher-priority? (vector-ref heap 2)] [vec (vector-ref heap 1)])`

Formalizing the problem
-----------------------

* Question: Given a non-net-neutral Internet and a starting node on the
  Internet and an ending node, find the cheapest way to get from the
  starting node to the ending node.
* Question: Given two cities and the cost of flying between any cites,
  find the cheapest set of flights between the first city and the last.

Formalize: What is the input?  What is the output?  What do we expect
of the output?

Input: 

* N, a series of nodes (distinct names or values)
* E, a cost function (an element of NxN to Z)
* s, an element of N (the starting point)
* t, an element of N (ending point)

Goal

* Find a sequence of nodes n_a_0 ... n_a_k s.t. n_a_0 = s,
  n_a_k = t, and [white board]

Selecting possible approaches
-----------------------------

_Talk to your group for a minute.  Be prepared to present two or
three ways we might start approaching the problem._

* Greed: Always choose the lowest cost next edge.
* Exhuastive search: List every path.
* Random: Pick any.
* Try sizes of paths in increasing order (0 then 1 then 2 then 3 ...)
* Divide and conquer.
* Just try something.

Question

* What do we do if there isn't an edge/connection?  E(a,b) = infinite.


Some sample solutions
---------------------

_I will assign approaches to groups.  Groups will have five minutes
to think about them and then present._

Analyzing the sample solutions
------------------------------

_We will then think about each._

### Greed

Greed does not work.  Consider a situation in which the smallest edge
leads you to a dead end (a node with only infinite cost edges).  Boom!

Fixing it:

* Add backtracking.  Sounds hard.
* Remove any nodes that are dead ends and are not the target node.

### Exhaustive search

1. Make a list of every possible sequence of nodes.  _How?_
2. Find the cost of each sequence of nodes using the summation.
3. Choose the least.  

Correct?
  : Yes

How expensive is this?
  : O(|N|*#sequence of nodess)

How many sequences of nodes are there?
  : Claim 1: |N|!
  : Claim 2: Infinite.  There might be cycles.

How do you fix the problem statement?
  : Next class!

### Random

Once in a while, we might get the best sequence of nodes.

A hint
------

_What if we wanted the shortest sequence of nodes from s to *every* node._

A more standard solution
------------------------
