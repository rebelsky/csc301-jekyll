Comparing Sorting Algorithms
----------------------------

Given two sorting algorithms, what are some criteria you might use
in deciding which is better for your particular applications.

Here are some I've come up with:

* Running time
    * Asymptotic: Expected
    * Asymptotic: Worst case
    * Actual
    * Based on distribution of data
* Stable or not
* Extra space required
* In place or out of place

O(nlogn) Sorting Algorithms
---------------------------

You should know three (plus or minus)

* Merge sort (top-down and bottom-up)
* Quick sort (well ...)
* Heap sort (we'll revisit this one on Monday)

Lower Bounds on Comparison-Based Sorting Algorithms
---------------------------------------------------

* The decision tree model!
    * We show the positions of the two values we compare
    * We have two choices: One is less than the other or one is
      greater than the other.  (We'll assume unique values wlog.)
    * We gather knowledge at each step.
    * At the leaves, we have instructions for permuting the original
* Let's build a decision tree of 3 values (class project)
* Generalize: How many leaves are there in a tree for an array of n
  values?
* What's the best case height for that tree?
