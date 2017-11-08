---
title: Eboard 30  Miniumum spanning trees, continued
number: 30
section: eboards
held: 2017-11-08
current: true
---
CSC 301.01, Class 30:  Miniumum spanning trees, continued
=========================================================

_Overview_

* Preliminaries
    * Notes and news
    * Upcoming work
    * Extra credit
    * Questions
* Note on algorithm design strategies
* Prim's algorithm and Kruskal's algorithm
* Proofs of correctness
* Efficiency

### News / Etc.

* I expect that most upper-level CS classes will fill this semester.
  You help the department better consider stress points and how to address
  them if you register earlier, rather than later.
* Some interesting courses to consider
    * Wilson short course: Human Centered Design for Global Social 
      Transformation
    * Wilson short course: Leadership in a Future of Automation and Income
      Inequality.
    * ENG 295-01. Lighting the Page: Digital Methods in Literary Studies.
      (ENG-120 prereq)
    * HIS 295-01.  Digital Methods in Historical Studies.  (HIS-100 prereq)

### Upcoming work

* [Assignment 8](../assignments/assignment08) due TONIGHT at 10:30 p.m.
* [Exam 2](../exams/exam02) due next Wednesday at 5:00 p.m.

### Extra credit (Academic/Artistic)

* Crip Technoscience, Disabled People as Makers and Knowers, Wednesday,
  Nov. 8, 4:15 p.m., JRC 101.
* Workshop by Sanjay Khanna '85 "Khanna can pitch.  Can you?" 
  Tonight at 7pm in ARH 120.  Sign up at
  <https://grinnell.co1.qualtrics.com/jfe/form/SV_8B7YaJkixNUBmjH>

### Extra credit (Peer)

* Pub-free Quiz, TONIGHT
* Virtual Food (and real food) event at VR club Saturday 6-8 in DLab
* VR club Sundays at 8pm in DLAB.

### Extra Credit (Misc)

### Other good things

### Questions

I can't apply the topological sort algorithm on a graph with a cycle.
  : Don't use a bootleg copy of the book.

What do you mean by "describe a graph"?
  : Give enough explanation that someone could draw/make it.

Can every DAG be expanded into a tree by repeating nodes?
  : I believe so.  But it can be exponentially larger.

A note on algorithm design strategies
-------------------------------------

* Divide and conquer: Divide the input in half (approximately).  Solve
  the problem for either or both halves.  Combine the solutions into a
  a solution for the overall problem.
    * Binary search
    * Merge sort
    * Quick sort
* "Greed" as a strategy
    * Given a group of choices, choose one that is obviously largest/smallest
    * If you've chosen greed as a strategy, you should decide how you
      are going to be greedy.
        * What's the set of values you choose among?
        * Do you choose largest/smallest
* One more strategy: Exhaustive search
    * Advantage: Correct
    * Disadvantage: Expensive
* Soon: Dynamic programming (fancy "caching")

Greedy approaches: Prim's algorithm, Kruskal's algorithm, and ...
-----------------------------------------------------------------

* Prim's: Throw away all the edges, pick a vertex, and repeatedly add 
  lowest weight edge that expands the tree of vertices reachable from 
  that vertex (and does not create a cycle).
    * Choose smallest
    * Set: Neighboring edges from the tree
    * Q: How do we know if we've made a cycle?    
        * Breadth-first exploration or depth-first exploration.
        * Expensive O(n+m)
    * In the typical implementation of Prim's, we mark nodes as we go.
      That means "check for cycle" is O(1).  Requires O(n) work at the
      beginning to unmark all of the vertices.
* Kruskal's Throw away all the edges, repeatedly add the lowest weight 
  edge that does not cause a cycle.  (Alternately: That connects two
  disconnected components)
    * Choose smallest from among *all* remaining edges
    * May have to do a more expensive operation to check if we are
      connected two disconnected components.
* Other: Repeatedly throw away the largest edge unless it disconnects 
  the graph.
    * Choose largest from among *all* remaining edges
    * Requires a connectivity check: O(n+m)

Proofs of correctness
---------------------

Suppose that we want to prove that one of these algorithms is correct.
What kinds of proof techniques might we try?

* Induction - Often useful in CS (if it works for a graph of size N,
  it should work for a graph of size N+1) (strong or weak)
* Contradiction - Assume it doesn't work.  Show that leads to a logical
  inconsistency.  "Suppose G(V,N') is not an MST ..."
* Constructive.  Building up from ground zero.  (Invariants)
* Prove the contraposative.  
* Reduce to known fact/proof.

Let's try proving that Kruskal's algorithm is correct.

* Suggested technique: Contradiction.
* Suppose Kruskal's algorithm is not correct.  
* That means that there exists a graph for which Kruskal's generates 
  an incorrect MST.
* Look at the MST for that graph.
* There exists an edge in the Kruskal Tree that is not in the MST.
* What happens when we add it to the real MST?  That creates a cycle.
  The Kruskal edge must have a lower weight than one other edge in the 
  cycle.  (O/w Kruskal would not have chosen it, since it would have
  considered all of the others first.)
* We can replace the heigher weight edge with the Kruskal edge and get
  a more minimal MST.  There aren't "more minmal" MSTs.
* Therefore our initial assumption was wrong.
* And Kruskal's algorithm is correct.

        +---+
        |   |
        +---+



Efficiency
----------

### Prim's

### Kruskal's

