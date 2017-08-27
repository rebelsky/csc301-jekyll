Designing a Graph ADT
---------------------

Reminder!  My goal is as much process as product.  Not just what you 
come up with, but also how you compare different approaches.

* Philosophy
* Use cases
* Methods

Discuss with your partners the three parts.  Plan to present methods.

* Think about both building graphs and accessing graphs.
* You might also consider related data types that you will need.
* Don't worry about providing implementations of common algorithms; you
  just want to assume that people can implement those algorithms using
  your ADT.

Different Perspectives on Graph ADTs
------------------------------------

* Do we build the graph all at once and then access elements, or do we
  dynamically change the graph as time goes on?  
* Does that affect how you design the ADT?

Building Graphs
---------------

* Add vertices (all at once?  one at a time?  implicitly?)
* Add edges (all at once?  one at a time?)
* Remove vertices?
* Remove edges?

Extracting Info from Graphs
---------------------------

* edge?(a,b)
* edge(a,b)
* Iterator&lt;Vertex&gt; vertices();
* Iterator&lt;Vertex&gt; neighbors();
* Iterator&lt;Edge&gt; edgesFrom(v)
* Iterator&lt;Edge&gt; edgesTo(v)

Implementing Graphs
-------------------

* Edge lists
* Adjacency lists
* Adjacency matrix
