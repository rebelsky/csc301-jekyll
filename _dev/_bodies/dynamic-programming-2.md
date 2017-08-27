An Implementation of the DP Solution to the Stamps Problem
----------------------------------------------------------

* See [examples/stamps.rkt](../examples/stamps.rkt)

The Knapsack Problem
--------------------

* Input: 
    * A bunch of items, each of which has a weight and a value.
    * A limit on the total weight.
* Output:
    * A subset of the items whose total weight is under the
      maximum weight
    * Having maximized the values.
    
The Edit Distance Problem
-------------------------

* What's the fewest number of edits (insertions, deletions) necessary
  to transform one string to another?
* Once again, there's a nice recursive formulation working from one
  end of the string (usually the back) to the other end of the string.
* Can we use dynamic programming techniques to make it iterative?
* This time, we need a two-dimensional table.
    * Rows: Letters of source string
    * Columns: Letters of target string
    * Moving up represents deletion
    * Moving lef represents insertion
* And yes, we should fill it in iteratively
