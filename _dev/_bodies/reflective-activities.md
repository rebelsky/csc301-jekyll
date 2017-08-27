Dijkstra's shortest-path algorithm, revisited
---------------------------------------------

*Slightly modified version of the version from Wikipedia, available at 
<https://en.wikipedia.org/wiki/Dijkstra%27s_algorithm>.*

<pre>
 1  function Dijkstra(Graph, source, target):
 2
 3    dist[source] = 0              // Distance from source to source
 4    prev[source] = undefined      // Previous node in optimal path initialization
 5
 6    create vertex set Q           // Unvisited nodes
 7
 8    for each vertex v in Graph:   // Initialization
 9      if v != source:             // (unvisited nodes)
10        dist[v] = INFINITY        // Unknown distance from source to v
11        prev[v] = UNDEFINED       // Previous node in optimal path from source
12      add v to Q                  // All nodes initially in Q (unvisited nodes)
13      
14    while Q is not empty:
15      u = vertex in Q with min dist[u]    // Source node in the first case
16      remove u from Q 
17          
18      for each neighbor v of u:   // where v is still in Q.
19        alt = dist[u] + length(u, v) // length of path through u
20        if alt < dist[v]:         // A shorter path to v has been found
21          dist[v] = alt 
22          prev[v] = u 
23
24    return dist[target]           // or the path using prev
</pre>

* What's the running time?  You can use _n_ for the number of nodes and
  _e_ for the number of edges.  (5 min with partner.)
* What's the core design strategy?

Algorithm design strategies, revisited
--------------------------------------

* We noted that we know divide-and-conquer as an algorithm design strategy,
  but are there others?
* What the underlying design strategy of Dijkstra's shortest path
  algorithm?
* What are underlying design strategies for other algorithms you know?
    * Merge sort?
    * Quicksort?
    * Selection sort?
    * Heap sort?

Greedy algorithms
-----------------

* Dijkstra's shortest path algorithm is an example of a *greedy* algorithm.
  (We probably noted that already)
* Given a choice, it always chooses the *smallest* value.  (Some greedy 
  algorithms always choose the *largest* value.)
* Have you seen any other greedy algorithms?  (2 min with partner.)
* Consider the robot motion problem.  Why doesn't the greedy algorithm
  work?
* What other alternatives are there when divide-and-conquer doesn't work,
  and neither does greed?

Asymptotic analysis, reviewed
-----------------------------

* What have you learned about asymptotic analysis?
* What does it mean for a function to be in O(n), theta(N), omega(N)?
* How does the formality relate to algorithm analysis?

Additional properties of Big-Oh
-------------------------------

* Prove that if f(n) is in O(g(n)) and g(n) is in O(h(n)) then
  f(n) is in O(h(n)).
* What other properties do you expect to be useful?
