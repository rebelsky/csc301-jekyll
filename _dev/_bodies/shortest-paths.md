The Shortest-Path Problem
-------------------------

The shortest-path problem is relatively straightforward: Given two nodes,
source and sink, an an edge-weighted graph, find the shortest path from
source to sink.

There are many variants: 

* We can have vertex weights rather than edge weights
* We can limit the edge weights (most typically, to non-negative values)
* We can look for multiple shortest paths
* We can find the length of the shortest path
* ...

Dijkstra's Shortest-Path Algorithm
----------------------------------

Dijkstra's works for graphs with non-negative edge weights, either
directed or undirected.  Instead of finding the shortest path from source
to sink, it finds the shortest path from source to every node.

    Node predecessor[n] // Predecessor on shortest path
    int distance[n]     // Distance to node; initialize to infinite
    boolean processed[n]// Have we processed node n.

    distance[source] = 0
    while there are unprocessed nodes
      find u, the unprocessed node with the shortest distance
      mark u as processed
      for each edge (u,v)
        if (distance[u] + weight[u,v] < distance[v])
          predecessor[v] = u
          distance[v] = distance[u] + weight[u,v]

An Example
----------

We'll probably generate a randomized graph on the fly.

Analyzing Dijkstra's Shortest Path Algorithm
--------------------------------------------

* How do we find the unprocessed node with the shortest distance?
* What's the running time?
    * Can we do better?
* How do we know that it's correct?
* How does this differ from Prim's algorithm?

All Pairs Shortest Path Algorithms
----------------------------------

How would you build a matrix of the lengths of all of the shortest
paths between any two vertices in a graph?

Floyd-Warshall
--------------

We will gradually build the matrix by looking at paths that only 
go through vertices 0 .. k.

Suppose we've correctly built the matrix for 0 .. k-1.  How do we
build the matrix for k?
