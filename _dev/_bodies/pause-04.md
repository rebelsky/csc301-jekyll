All Pairs Shortest Path, Continued
----------------------------------

Reminder: The Floyd-Warshall algorithm makes a sequence of matrices,
matrix k is the matrix which gives shortest paths involving only
intermediate nodes numbered 0..k.

Question: How do we construct matrix k+1 from matrix k?

Question: Will this work with negative edges (but no negative cycles)?

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

