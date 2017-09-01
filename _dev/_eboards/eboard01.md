---
title: Eboard 01  An introduction to the coure
number: 01
section: eboards
held: 2017-08-25
---
CSC 301.01, Class 01:  An introduction to the coure
===================================================

_Overview_

* Preliminaries
    * Notes and news
    * Upcoming work
    * Extra credit
    * Questions
* Course goals
* Course format
* Approaching algorithms.
* Problem: Getting from here to there
* Problem: Optimal soldering plans
* Problem: Scheduling overlapping tasks

### News / Etc.

* Welcome back!  I look forward to having an excellent semester with
  you all.
* I will take quick attendance.
* I expect all of you to sign the department's academic honesty policy.
  Please turn it in by Wednesday.
* As is typical for the start of the semester, the course Web site is
  in rougher shape than I would like.  Expect it to take form over the
  next few weeks.
* I will be using the white board more than in other classes, particularly
  since I will be drawing data structures.  Do you want to share daily
  note-taking responsibilities?  We will revisit the question on Monday.
* Friday PSA.
   
### Upcoming Work

* Read chapter 1 of Skiena by Monday.
* [Homework 1](../assignments/assignment01), due Wednesday 

### Extra Credit

#### Academic

* CS Table, *Tuesday*, topic tbd.
* CS Extras, *Thursday*, Contracts.

#### Peer

### Good things to do

* Ag days next Thursday.

### Questions

How do we report on extra credits?
  : If you attend one, send me a short (one-to-two paragraph) email
    within two days of the event.
  : I prefer that you send me announcements in advance of class.

Course Goals
------------

* Think of it as "207, enhanced/extended/made more challenging"
* Learn how to design and analyze algorithms and data structures.
    * Tools (methodologies for design, examples)
    * Verification techniques
    * Think about efficiency and how you analyze it carefully
* More of the core literature
    * You already know trees, merge sort, Quicksort, binary search
      map/reduce, priority queues, priority queues implemented as heaps,

Detour priority queues
----------------------

Idea: Implement priority queues as lists that are sorted from highest
priority to lowest.

* Add "Learn about heaps, priority 5"
* List with (heaps/5) at the front.
* Add "Study for the CSC 301 final, priority 1000"
* List of the form [(heaps/5),(301final/1000)]
* How much time does it take to put something in the right place in this
  list?
     * O(n^2)
     * O(nlogn)
     * O(n)
     * O(logn) (+1)
     * O(1)

Course Format
-------------

Often, Sam will pose problems and let you work on them and present them.

* Incredibly supportive random calling on people
* Small group work

Approaching Algorithms
----------------------

*You are now experienced computer science students.  When some gives
you a problem that admits an algorithmic solution, what do you do?*

Think->Pair->Share

Approach one -> Getting from point A to point B

* There are places along the way from point A to point B, think about
  the places along the way and how you get from point A to the next
  point to the next ...
* More generally, break the problem up into smaller problems.
* Once you have a solution, go back and see if you can make it better.
* Top-down decomposition

Approach two -> Just try something

* Kind of like freewriting in English.  Get something out there.

Approach three -> Use the literature

* Identify similar problems that might give you insight on how to
  solve this problem.

Approach four -> Try examples

* Solve some examples of the problem by hand to gain insight.

Approach five -> Use a standard algorithm design strategy

* Divide and conquer
* Greed
* We wll learn others

Additional things to help any approach

* Make sure that you understand the problem
    * Formal specs
    * Unit tests
    * Talking to people
* Draw pictures
* Make sure that it's correct
* Consider how efficient it is

Problem: Getting From Here to There
-----------------------------------

* Let's pretend that net neturality is eliminated.
* We now have a problem: We need to get information from place to place,
  and we may want the least expensive path, or the quickest, or ...

We start by modeling the the problem

* How do you represent/think about the input?
* This is probably a weighted graph problem.
* A graph is a collection of points ("nodes", "vertices") that have
  connections between them ("edges").
* Weighted graphs include a value associated with each edge.
* Problem: Find the path (sequence of edges) from A to B with the least
  total cost.

Problem: Optimal Soldering Plans
--------------------------------

**Skipped**

*Stolen/modified from Skienna*

* We have a bunch of points that we need to have a robot solder
  on a circuit board.
* We want the least wear and tear on the robot.
* How do we determine how to order the points?

Problem: Scheduling Overlapping Tasks
-------------------------------------

**Skipped**

*Stolen/modified from Skienna*

* You have a bunch of tasks, each of which has a start time and a length.
* You can only do one task at a time.
* How do you maximize the number of tasks you complete?

Extension

* What if each task also has a value?  How do you maximize the value
  of the tasks you complete?

