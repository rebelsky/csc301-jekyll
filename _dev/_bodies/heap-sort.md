Background
----------

* We are considering O(nlogn) sorting algorithms.
* Merge sort is guaranteed O(nlogn), but requires O(n) extra space.
* Quicksort requires O(1) extra space, but is not guaranteed to be
  O(nlogn)
* Can we have something that uses O(1) extra space and is
  guarateed O(nlogn)
* Priority queues provide obvious sorting algorithms
* A really good implementation of priority queues can give a fast
  sorting algorithm
* A spectacularly good implementation of priority queues can provide
  in-place sorting.

Heaps
-----

* Something like search trees, but different.
* Binary trees with *the heap property*
    * Each node is at least as big as the roots of its subtrees.
    * Each subtree also has the same property.
* Binary trees that are *nearly complete*
    * It's complete in the sense that most nodes have two children
    * At the last level all the nodes are at the left.
* Check in: Which of the following are heaps (drawn on whiteboard)

Adding Elements
---------------

* Two invariants to maintain: The shape of the tree and the heap property.
     * Which is harder?  Probably getting the shape right.
* So we add an element at the end of the last level.
* And then we restore the heap property by repeatedly swapping up.
* Sample tree: Build with eight or so numbers.

Removing Elements
-----------------

* The largest (highest priority) element is at the top.
* Once we remove it, what do we do?
* Once again, two invariants to maintain: The shape of the tree and the
  heap property.
* So, we take the last element and put it at the root.
* And then we swap it down to the right place?
    * Repeatedly swap with the larger child (provided it's smaller than
      the larger child).
* Exercise: Remove the three largest values  from our tree.

Using Arrays
------------

* But how do we know where the last element on the last row is (for
  both insertion and removal)?
* Here's the really clever part: We can store heaps in arrays.
* Can you figure out the index of children and parents?
* And once we use arrays, we can build and destruct the heaps *in place*

