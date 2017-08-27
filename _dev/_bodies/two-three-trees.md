2-3 Trees
---------

* Another approach to balanced binary search trees.
* Nodes can have one or two values and two or three subtrees
* Nodes with one value and two subtrees are just like normal BST nodes.
* Nodes with two values have the property that
    * All values in the left subtree are less than the first value
    * All values in the middle subtree are between the two values.
    * All values in the right subtree are greater than the second value.
* To maintain balance, each subtree must be the same height.

Insertion in 2-3 Trees
----------------------

_In thinking abou this, you might want to generate a list of random numbers 
and think about what you would do as you add each of the random numbers._

* We will insert only at the leaves.
* What are the cases?
* What should we do in each of those cases?
* Which cases require "propagating changes up"?
* What cases require rotation?

Deletion in 2-3 Trees
---------------------

_In thinking about this, you might want to build a medium-sized 2-3
tree and then delete each node as you go._

* We can delete anywhere
* What are the cases?
* What should we do in each of those cases?
* What cases require "propagating changes up"?
* What cases require "propagating changes down"?
* What cases require rotation?

Generalizing 2-3 Trees: B-Trees
-------------------------------

* Instead of just 2 values, we permit beween m and n values in the node
  (so between m+1 and n+1 subtrees).
* Why use this model?  It acknowledges that for big trees, we'll be
  storing them on disk, so we might as well take advantage of the size
  of a typical disk block.
* But the model of insertion and deletion will be very similar.
