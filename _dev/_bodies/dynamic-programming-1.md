The Stamps Problem
------------------

* Given some set of stamp values and a desired value, find the
  fewest stamps to make that value.
    * E.g., with 1, 2, 7, 12, 25 make 28 or 36.
* It's relatively straightforward to phrase this recursively.

Dynamic Programming
-------------------

* A mechanism for dealing with problems that have elegant but expensive
  recursive formulations.
* Traditionally, two main steps:
    * Design a table (usually one-dimensional or two-dimensional)
      to cache intermediate results.
        * Check the table when making a recursive call.
    * Rewrite the algorithm to build the table iteratively rather than
      recursively.
* We can apply dynamic programming to the stamps problem.

The Knapsack Problem
--------------------

* Input: 
    * A bunch of items, each of which has a weight and a value.
    * A limit on the total weight.
* Output:
    * A subset of the items whose total weight is under the
      maximum weight
    * Having maximized the values.
    
