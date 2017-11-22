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
* Three+ implementations of graphs

### News / Etc.

* I expect that most upper-level CS classes will fill this semester.
  You help the department better consider stress points and how to address
  them if you register earlier, rather than later.

### Upcoming work

* Exam 2 prologue due TONIGHT.
* [Exam 2](../exams/exam02) due Wednesday at 5:00 p.m.

### Extra credit (Peer)

* Pub-Free Quiz, Next Wednesday
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

_Asymptotic analysis: n is number of nodes, m is number of edges._

* We can assume that it costs O(1) to add a node or edge to our MST.

Prim's: Throw away all the edges, pick a vertex, and repeatedly add lowest
weight edge that expands the tree of vertices reachable from that vertex
(and does not create a cycle).

* Note: We can mark the nodes that are in the MST, so the cost of
  "should we add this edge?" is O(1).
* Loop: 
    * Find lowest weight edge in fringe of MST - O(logm)
    * Check if it is useful, if so - O(1)
        * If so, add it to the MST - O(1)
        * And add all the neighboring edges to the heap representing the
          fringe O(nlogm)
* How many times does the loop run?
    * O(n), because we have to make sure that every vertex is reached.  NO
    * O(m), ignoring the "if so" costs
* How do we find the lowest weight edge in the fringe: Store them in a
  heap.  O(logm) to find the minimum.
* If we ignore the cost of adding to the heap, this is O(mlogm)
* We add each edge to the heap at most twice, so O(mlogm) to add to the heap.

Kruskal's Throw away all the edges, repeatedly add the lowest weight 
edge that does not cause a cycle.  (Alternately: That connects two
disconnected components.)

* Note: The marking trick does not work here.
* Note: We will add n-1 edges
* Sort edges: O(mlogm)
* Loop - for every edge
    * Grab lowest weight edge
    * Check if connects disconnected components
* How do we check if it's connected?
    * Option 1: Do a BFS or DFS.  If you visit every node, it's connected.
      If you don't, it's not connected.  O(m+n)
    * Observation: The MST we've built only has O(n) edges, so it's
      really only O(n) to check if it has a cycle
    * In that case, running time is O(m*n)
    * Option 2: Use a union-find data structure (which we haven't learned
      yet).  Finding connected components in a union find data structure
      is O(log(k)), where k is the number of nodes in the structure.
    * In that case, running time is O(m*logn)

What is the relationship of n to logm?  

* We have a connected graph, so we know that m >= n.
* The largest m could be is O(n^2)  log(n^2) = 2logn.
* Would you rather m*n or m*2*log(n)
* log(n) is better than n.  2log(n) is also much better than n.

Some learning outcomes

* Analyzing graph algorithms means paying attention to some subtleties.
* Doing analysis *might* help us better understand the algorithm.
* We often need helper data structures or good tricks to make it efficient
    * Prim's: Heap, mark nodes for checking cycles
    * Kruskal's: Union-Find

Key graph operations
--------------------

Three+ implementations of graphs
------------------------------

* Edge list: List of edges (plus a list of nodes)
* Adjancency list: List of nodes, each of which has a list of outgoing
  edges.
    * Issue: How do you go from an edge to a node?
    * Solutions: 
        * The list is really a hash table (or other dictionary)
        * Use pointers rather than names
* Adjacency matrix: nxn grid.  matrix(x,y) is the weight of the edge from
  x to y.
* For a sparse adjaceny matrix ... you could use a hash table where
  the keys are (node,node) pairs.


