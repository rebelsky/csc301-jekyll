Analyzing Kruskal's Algorithm, Revisited
----------------------------------------

    sort the edges by weight
    while the graph is not connected
      find the smallest weight edge that connects two components

* `m` rounds.  At each round we inspect an edge and decide whether or
  not to add it to the MST.
* We add it only if it connects two different components.
* How much does it cost to determine whether an edge connects two different
  components?

Sets
----

* We can treat each component as a set of values.
* That means we should probably think about ADTs.
* Guess what: That's your responsibility.

Union-Find
----------

* Implementing a subset of the set operations.
* `Union(s1,s2)`: Given two sets, destructively create their union.  (I'd
  call this merge, but that's me.
* `Find(v)`: Determine what set a value is in.
