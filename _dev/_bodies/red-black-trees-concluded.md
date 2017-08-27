Key Ideas from Insertion
------------------------

* A common strategy for developing data structure: Place some requirements
  on the data structure, look at the requirements that are violated after
  certain operations, figure out how to restore those requirements.
* Note that we relied on something very much like loop invariants
    * The "black height" property was restored after every step.
    * The "red-black" proeprty held below each point.
    * At every "step", we move higher in the tree.
* These ideas do not come easily.  It is like mathematics in that way ...
  you try something.  You may seem to move forward.  But you then hit
  a dead end.  So you back up, and try something again, and again, and
  again.  
* Sometimes you solve some cases one way and solve the rest by transforming
  into already solved cases.

Deleting from BSTs
------------------

* Some deletions are easy (typically near leaves), some are not so easy.
* Multiple approaches.
    * There's one I taught my students
    * CLRS show a general one that seems more efficient.

Deleting from Red-Black Trees
-----------------------------

* The scary line: "Deleting a node from a red-black tree is a bit more
  complicated than inserting a node."
* But it's not too bad, as long as we keep track of all of the details.
