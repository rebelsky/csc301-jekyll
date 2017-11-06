---
title: Eboard 29  Minimum spanning trees
number: 29
section: eboards
held: 2017-11-06
---
CSC 301.01, Class 29:  Minimum spanning trees
=============================================

_Overview_

* Preliminaries
    * Notes and news
    * Upcoming work
    * Extra credit
    * Questions
* Minimum spanning trees
* Examples
* Designing an MST algorithm
* Prim's algorithm and Kruskal's algorithm
* Efficiency
* Proofs of correctness

### News / Etc.

* Sorry about the temrporarily broken Web site.  The Bootstrap style I used
  changed unexpectedly.  (I hear it broke many of the Course webs in the
  department.)
* Sorry that I could not be in class on Friday.
* I expect that most upper-level CS classes will fill this semester.
  You help the department better consider stress points and how to address
  them if you register earlier, rather than later.
* No, grading is not done.  Thursday, Friday, Saturday, and half of
  Sunday were booked.  I spent six hours grading, but that's not enough.
    * Weekdays are booked 8:30-5:00 (and it's preregistration)
    * Tonight: Write draft of your exam.  Write 151 project description.
      (Skip concert.)
    * Tuesday: CSC 151 exam grading.
    * Wednesday: CSC 151 exam grading.
    * Thursday: (Maybe) CSC 301 exam grading.
* I have more on the agenda for today than I expect we will cover.  
  Wednesday's class will catch the overflow.

### Upcoming work

* [Assignment 8](../assignments/assignment08) due next Wednesday at 10:30 p.m.
  (All written problems!)

### Extra credit (Academic/Artistic)

* Leyla McCalla Trio, Nov. 6, 7:30 p.m. Herrick
* Animated Films, Tuesday, Nov. 7, 11:00 a.m., Faulconer
* CS Table (Computer-Aided Gerrymandering), Tuesday, Nov. 7, noon, 
  Day Dining Room
* Crip Technoscience, Disabled People as Makers and Knowers, Wednesday,
  Nov. 8, 4:15 p.m., JRC 101.

### Extra credit (Peer)

* VR club Sundays at 8pm in ???.
* Not-Pub Quiz?

### Extra Credit (Misc)

### Other good things

### Questions

Minimum spanning trees
----------------------

Given a weighted non-directed connected graph, G(V,E), build a new
connected graph G(V,E'), s.t.

* E' is a subset of E.
* If G(V,F) is connected and F is a subset of E, the sum of the weights
  in F is less than or equal to the sum of the weights in E'.

Why is it called a minimum spanning *tree* rather than a minimum 
spanning *graph*?

Designing an MST algorithm
--------------------------

How might you approach the problem?  (Once we've come up with some
approaches, we'll assign approaches to different groups.)

Examples
--------

Here's a graph!  (Picture on the board.)

```
Vertices: A, B, C, D, E, F, G
Edges: AB(6), AC(7), AE(8), BD(9), CD(1), CE(1), CF(2), DF(5),
EF(10), EG(14), FG(8).
```

Approaches, Revisited
---------------------

Prim's algorithm and Kruskal's algorithm
----------------------------------------

Efficiency
----------

Proofs of correctness
---------------------

