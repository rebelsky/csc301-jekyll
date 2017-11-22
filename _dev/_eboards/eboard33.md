---
title: Eboard 33  Network flows
number: 33
section: eboards
held: 2017-11-15
---
CSC 301.01, Class 33:  Network flows
====================================

_Overview_

* Preliminaries
    * Notes and news
    * Upcoming work
    * Extra credit
    * Questions
* Looking back to graph algorithms
* Network flows
* Bipartite matching

### News / Etc.

* The due date of Exam 2 has been pushed to Friday.

### Upcoming work

* [Exam 2](../exams/exam02) due Friday at 4:00 p.m.
* Read the rest of Skiena 6 for Friday.

### Extra Credit (Academic/Artistic)

* Convocation Thursday at 11 a.m. in JRC 101.  "Work's Provocative Future: 
  Which Graduates Will Thrive?"

### Extra credit (Peer)

* Pub-Free Quiz, TONIGHT at 9pm, with a Stats-Math theme
* Swim and dive meet, Saturday

### Extra Credit (Misc)

### Other good things

* "The First Time I Walked on the Moon".  Thursday 7:30, Friday 7:30,
  Saturday 2:00, Saturday 7:30, Sunday 2:00.
* Fresh Flutes Thursday
* Voice recitals Friday at 4:15 (Henderson) and 7:00 (Manuel)
* Orchestra Saturday at 2pm
* Women's Basketball vs. Emmaus Wed at 5:00 p.m.
* Men's Basketball vs. Emmaus Wed at 7:00 p.m.

### Mentor Evaluations


Looking back to graph algorithms
--------------------------------

### Kruskal's MST algorithm.

* Sort the edges by weight from smallest to largest.
* For each edge in the list of the sorted list,
    * If it joins two disjoint subgraphs, add it to the MST

Note: We check if two subgraphs are disjoint using union find.

French's claim: You can use Kruskal's to count the number of connected
components in a graph, assuming that a lone vertex *is* a connected
component (or not, whichever is easier).

_How_?

* You are using union find, so count how many sets there are in union
  find.  (How?  Keep a list.)
* Easier (without union-find structure): There are n-1 edges in a MST
  in a connected graph of N nodes.  Suppose there are n-2 edges in the
  MSF (minimum spanning forest).  Suppose there are n-3 in the MSF?
* Adding an edge connects two components.  If we add n-k edges, we have
  k components.

### Union find details

* A is union-find structure with 7 nodes and depth 1.  B is a union-find
  structure with 6 nodes and depth 4.  Which should become the root?
  Why?
* B: 
    * Claim: Attach the shorter tree to the taller tree.  Otherwise O(n).
    * Makes it shallower overall.
* A: 
    * When we clean up after doing a find, we'll have fewer nodes to fix.
* When Sam implments union find data structures, he chooses the one with
  more nodes (bigger size) as the root.  Why?  
    * I can still guarantee that the height is logarithmic.
      (Any subtree contains at most half of the nodes.  The rest is
      obvious by induction.)
    * Updating the size when simplifying is much easier than updating
      the height.

Network flows
-------------

Given a directed weighted graph, a designated starting point, s, and a
designated ending point, t, find a set of weights on the edges such that
(a) no weight in the new graph is greater than the original weight of the
edge and (b) we maximize the total "flow" from s to t, measured by the
total number of things coming in to t.

How do you find this somewhat ill-defined thing?

* S->A: 4
* A->B: 3
* B->T: 8
* S->C: 5
* C->D: 7
* D->T: 3
* D->B: 2
* C->A: 6

Idea: 

* For each edge, we will keep track of how much capacity we've used so far 
  and how much capacity remains.
* Repeat
   * In the graph of remaining capacity, find a path from s to t.
   * Find the smallest remaining capacity along that path.
   * Update usage on every edge by that amount.

This algorithm, while nice, is incorrect.

* The first time we ran it, we found a flow of 8.
* The second time, we found a flow of 5.
* It depends on which path you started with.


Think about how to solve that problem.

Bipartite matching
------------------

