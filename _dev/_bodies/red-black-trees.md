Balancing Binary Search Trees, Continuedj
-----------------------------------------

How do we keep trees balanced?  Let's start by thinking about some 
slightly imbalanced trees.  Lowercase letters will represent values,
uppercase letters will represent trees.  Numbers in parentheses 
represent the height of a tree

           a(n+3)
            / \
           /   \
        b(n+2) C(n)
         / \
        /   \
     D(n+1) E(n)

How did you balance this?

What are all options you can come up with for adding a leaf that will
cause an imbalance?

What whould we do in each case to achieve better balance?

Red-Black Trees
---------------

* Binary search trees in which every node is colored red or black.
  (The color can change.)
* The root is black.
* Leaves are null and are all black.
* Every red node has a black child.  (Black nodes can have red or black
  children.)
* For any node, n, the number of black nodes on the path from n to any
  of its leaf descendants is the same.  (Different nodes will naturally
  have different path lengths.)  We call this the *black height* of a
  node.
    * How do you compute the black height of a node?
* Example: CLRS p. 310
    * Is this a red-black tree?
    * What the is black height of each node?
* Why do we care?
    * Intuitively, the longest path from root to leaf cannot be more
      than two times the length of the shortest path from root to leaf.
      (They get longer the more reds we insert.)
      as long

Exercises
---------

_These are taken from CLRS._

* Draw the complete binary tree of the integers [1... 15] (so it's
  perfectly blanced.)
    * 1/3 class; Color the nodes so that it has a black height of 2
    * 1/3 class: Color the nodes so that it has a black height of 3.
    * 1/3 class: Color the nodes so that it has a black height of 4
* What happens if we add node 36 to our sample tree?
    * If it's red?
    * If it's black?

Insertion
---------

* Assumption: We make any node we insert red!
* What could go wrong?  
* We'll look at a series of examples based on trees of size 4
