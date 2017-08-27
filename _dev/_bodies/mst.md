Minimum Spanning Trees
---------------------

* Minimum spanning tree: Given a connected weighted graph, G(E,V), pick a
  subset of the edges, E', such that (a) G(E',V) is connected and (b)
  for any other subset of edges, F, weightsum(F) >= weightsum(E).
* What algorithmic approaches do we have?
    * Find similar algorithms
    * Divide and conquer
    * Greed
* Which is most likely to be useful?

Prim's Algorithm
----------------

* A greedy algorithm.
* Divide the vertices in the graph into those in the MST and those not
  in the MST.
* Repeatedly add the shortest edge from MST to non-MST.
* Practice (stolen from Walker):

     Vertices: A, B, C, D, E, F, G
     Edges: AB(6), AC(7), AD(8), BD(9), CD(1), CE(1), CF(2), DF(5),
     EF(5), EG(14), FG(8).

* Why is Prim's algorithm correct?
    * What proof techniques do you know?
* How efficient is Prim's algorithm in the abstract?
* What assumptions have we made about the underlying operations?
* Can we choose particular implementations to make it more efficient
  (assume we can use vertices as indicies into tables)?

Kruskal's Algorithm
-------------------

* Another greedy algorithm.
* Identify each connected component (initially n different ones, because 
  we have no edges)
* Repeatedly the smallest edge remaining that connects to separate components.
* Practice (stolen from Walker):

     Vertices: A, B, C, D, E, F, G
     Edges: AB(6), AC(7), AD(8), BD(9), CD(1), CE(1), CF(2), DF(5),
     EF(5), EG(14), FG(8).

* Why is Kruskal's algorithm correct?
* How efficient is Kruskal's algorithm in the abstract?
* What assumptions have we made?
* Can we use particular data structures to make it more efficient?
