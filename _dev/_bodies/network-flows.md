The Max-Flow Problem
--------------------

Problem: Given a weighted directed graph and two nodes (source and
target), find the maximum "flow" from the source to the target, where
we think of the weight of each edge as the capacity of that edge.
(This is a good simplified networking problem.)

We typically build a separate flow graph from the weighted directed graph.

Augmenting Paths
----------------

Most Max-Flow algorithms work with what is called an *augmenting path*.
That's a path from the source to the target in which each edge weight 
is positive.  

Here's an *incorrect* algorithm for building a max-flow graph

    while an augmenting path exists from source to target
      find the lowest edge weight on that augmenting path
      decrement each edge in the path in the original graph by that amount
      increment each corresponding edge in the flow graph by that amount

We'll do an example.

Why is the algorithm incorrect?

The Ford-Fulkerson Algorithm
----------------------------

    while an augmenting path exists from source to target
      find the lowest edge weight on that augmenting path
      decrement each edge in the path in the original graph by that amount
      increment each back edge in that path by that amount
      increment each corresponding edge in the flow graph by that amount

Note that this can be insanely inefficient.  See the Interweb for examples.

Bipartite Matching
------------------

Given two sets of vertices, L and R connected by unweighted edges, find a 
set of edges such that each element in L is connected to at most one element
in R, and each element in R is conntected to at most one element in L.

Solve this using max flow.
