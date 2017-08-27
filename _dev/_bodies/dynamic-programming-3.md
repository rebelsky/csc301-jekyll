The Knapsack Problem
--------------------

* What changes did you have to make to the Scheme code to get a 
  working solution?

The Edit Distance Problem
-------------------------

* What's the fewest number of edits (insertions, deletions, transformations) 
  necessary to transform one string to another?
* Once again, there's a nice recursive formulation.
    * We working from one end of the string (usually the back) 
      to the other end of the string.
    * We can transform all-but-the-last-character of the source string
      to all-but-the-last-character of the target string and then
      transform the last character of the source string into the
      last character of the target string.
    * We can delete the last character in the source string and then
      transform the remainder of the source string into the target
      string.
    * We can transform the source string into all-but-the-last-character
      of the target string and then add the last character of the target
      string.
* Can we use dynamic programming techniques to make it iterative?
* This time, we need a two-dimensional table.
    * Rows: Letters of source string
    * Columns: Letters of target string
    * Moving up represents deletion
    * Moving left represents insertion
    * Moving diagonally represents replacement
* And yes, we should fill it in iteratively
