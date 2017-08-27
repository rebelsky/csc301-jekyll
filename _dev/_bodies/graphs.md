Leftover Topics: Tries
----------------------

* What ADT does the trie implement?
* What are the relative advanges of tries vs. hash tables?

Graphs: Conceptual
------------------

* The world is connected.  
* You will find it useful to model many kinds of problems in terms of
  sets of connections.
* We call the things that are connected *nodes* or *vertices*.
* We call the things that connect nodes *edges*.
* Sometimes folks call graphs *networks*.
* We can ask all sorts of questions about graphs and networks.
    * Can we get from a vertex to another vertex?
    * Can we get from a vertex to every other vertex?
    * Can we get from every vertex to every other vertex?
    * What's the shortest route from one vertex to another vertex?
    * ...
* We can also look at different characteristics
    * Simple vs. Non-Simple
    * Sparse vs. Dense vs. Complete
    * Cyclic vs. Acyclic
    * Connected vs. Non-connected
    * Embedded vs. Topological
    * Labeled vs. Unlabled

Traversing Graphs
-----------------

* Goal: Visit all the vertices (and, often, edges) in a graph
* Typically keep track of three states for each vertex:
     * undiscovered: we have not looked at the vertex
     * discovered: we've looked at the vertex, but have not dealt with
       all of its edges
     * processed: we've looked at all of the edges
     

Graphs: ADT
-----------

We'll work together to generate an ADT.
