Review
------

* What is a red-black tree?
* Why do we care about them?
    * Depth is O(logn)
* What are the key operations?
    * Lookup
    * Insert
    * Delete
* What is the likely model for insert?
* What is the likely model for delete?

Student Questions
-----------------

* What parts of the reading made the least sense?

Insertion in Red-Black Trees
----------------------------

* We start by inserting using the normal BST insertion algorithm.
* We color the resulting node red.
* What properties might we have violated?
    * If we inserted at the root, we've violated the "black root" property.
    * If we inserted at a leaf, we might have violated the "red parents
      don't have red children" property.
    * Adding a red node should not change the number of black nodes on a
      path from node to leaves.
* What are the approaches we can use to make the tree closer to meeting
  the red-black criteria?
    * We can recolor nodes
    * We can rotate parts of the tree left or right
* What are the different cases in which trees might violate the "no two
  red nodes in sequence" property?
    * CLRS list three cases, but there are really eight cases (with some 
      symmetry).  

<pre>
01       b
       /   \
      r     r
     / \   / \
    ?   R ?   ?
       / \
      ?   ?
</pre>

<pre>
02       b
       /   \
      r     r
     / \   / \
    R   ? ?   ?
   / \
  ?   ?
</pre>

<pre>
03       b
       /   \
      r     b
     / \   / \
    ?   R ?   ?
       / \
      ?   ?
</pre>

<pre>
04       b
       /   \
      r     b
     / \   / \
    R   ? ?   ?
   / \
  ?   ?
</pre>

<pre>
05       b
       /   \
      r     r
     / \   / \
    ?   ? R   ?
         / \
        ?   ?
</pre>

<pre>
06       b
       /   \
      r     r
     / \   / \
    ?   ? ?   R
             / \
            ?   ?
</pre>

<pre>
07       b
       /   \
      r     r
     / \   / \
    ?   ? R   ?
         / \
        ?   ?
</pre>

<pre>
08       b
       /   \
      r     r
     / \   / \
    ?   ? ?   R
             / \
            ?   ?
</pre>

* The last four are symmetrical, so we won't process them?
* What are the black heights of the unnamed subtrees (or all the subtrees)?
* How do we change each?

Deletion in Binary Search Trees
-------------------------------

* What do you remember?
* Handout!

Deletion in Red-Black Trees
---------------------------

* Complicated!
