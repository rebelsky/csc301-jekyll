---
title: Eboard 31  Implementing graphs
number: 31
section: eboards
held: 2017-11-10
---
CSC 301.01, Class 31:  Implementing graphs
==========================================

_Overview_

* Preliminaries
    * Notes and news
    * Upcoming work
    * Extra credit
    * Questions
* MSTs, concluded
* Key graph operations
* Four implementations of graphs
* Associated costs

### News / Etc.

* I expect that most upper-level CS classes will fill this semester.
  You help the department better consider stress points and how to address
  them if you register earlier, rather than later.

### Upcoming work

* Exam 2 prologue due TONIGHT.
* [Exam 2](../exams/exam02) due Wednesday at 5:00 p.m.

### Extra credit (Peer)

* Not-Pub Quiz, Next Wednesday
* VR club Sundays at 8pm in DLAB.
* VR club open house Saturday 6-8pm in DLAB.

### Extra Credit (Misc)

### Other good things

* NM Voice tonight at 7:30 p.m.
* Showvember tonight
* Drag tomorrow

### Questions

MSTs, concluded
---------------

Prim's: Throw away all the edges, pick a vertex, and repeatedly add lowest
weight edge that expands the tree of vertices reachable from that vertex
(and does not create a cycle).

* Note: We can mark the nodes that are in the MST, so the cost of
  "should we add this edge?" is O(1).

Kruskal's Throw away all the edges, repeatedly add the lowest weight 
edge that does not cause a cycle.  (Alternately: That connects two
disconnected components.)

Key graph operations
--------------------

Four implementations of graphs
------------------------------

Associated costs
----------------

