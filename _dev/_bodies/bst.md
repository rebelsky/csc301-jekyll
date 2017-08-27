Trees, Formalized
-----------------

We all have an informal notion of what a tree is.  However, as we design
more careful algorithms, we also need to think more formally about the
definition of trees.

_Pause!  How might you define trees using formal notation?_

Here's what I might say.  (I assume the natural numbers start with 0.)

> A tree is triplet, `<V,r,child>`, where `V` is a set, `r` is
  a designated element of `V`, and `child` is a relation (set of tuples
  of the form `<p,c>`) in which `p` and `c` are elements of `V` subject
  to the following restrictions.  (For the relation, we might also write
  `child(p,c)`.)

> i. There exist no `v` such that `<v,r>` is in `child`.
  (*The root is not the child of any other value.*)

> ii. For all `v` in `V` not equal to `r`, there exists exactly one `p`
  in `V` such that `<p,v>` is in `child`.  (*Every value has exactly
  one parent.*)

We might also have *ordered trees*, in which we number the children.

> A tree is triplet, `<V,r,child>`, where `V` is a set, `r` is
  a designated element of `V`, and `child` is a relation (set of tuples
  of the form `<p,i,c>`) in which `p` and `c` are elements of `V` and
  `i` is an element of the natural numbers, subject to the following
  restrictions.

> i. There exist no `v` and `i` such that `<v,i,r>` is in `child`.
  (*The root is not the child of any other value.*)

> ii. For all `v` in `V` not equal to `r`, there exist exactly one `p`
  in `V` and `i` in the natural numbers such that `<p,i,v>` is in
  `child`.  (*Every value has exactly one parent.*)

> iii. For all `p` in `V` and `i` in the natural numbers, there is at
  most one `c` in `V` such that `<p,i,c>` is in `child`.  (*Each parent
  has at most one ith child.*)

> iv. For all `p` in `N` and `i` > 0, if there exists an `c` such that
  `<p,i,c>` is in `child`, then there exists a `b` such that
  `<p,i-1,b>` is in `child`. (There are no gaps in the children.)

Terminology
-----------

These are (mostly) informal.

* The designated value is called the *root*.
* Any value with no children is called a *leaf*
* The first element of a tuple is called the *parent*.
* The last element of a tuple is called the *child*.
* In ordered trees, the second element is called the *child number*.
* A *path* is a sequence of `child` tuples with the obvious properties (e.g.,
  that the parent or child of one is the parent or child of the next
  one).
* The *length* of a path is the number of tuples in the path.
* The *depth* of a value is the length of the shortest path from the root
  to that value.
* The *height* of a value is the length of the longest path from that
  value to a leaf.  (The height of a value is 1 + the maximum height of 
  it's children.)
* The *height* of a tree is the height of its root.
* All the values of the same depth are considered a *level* of the tree.
* Two values with the same parent are considered *siblings*.  If the 
  child relationship includes an ordering, children with lower indices
  are *left siblings* and children with higher indices are *right siblings*.
* A value `z` is a *descendent* of a value `a` if there exist a series
  of values `v_0`, `v_1`, ..., `v_(n-1)`, `v_n` 
  such that for all `i` in `[0..n)`, `<v_i,v_(i+1)>` is in `child`,
  `v_0` = `a`, and `v_n` = `z`.

Binary Trees
------------

For binary trees, we say that each value has at most two children.  
(We limit `i` to `0` or `1`.)  We often designate the child relationships
as `left` and `right`, rather than `child`.  We don't usually require
that nodes have both left and right children (removing restriction iv.

Traversing Trees
----------------

We normally speak about this in terms of the order in which we *process*
values, rather than the order in which we visit them.

* Breadth first vs. depth first.
    * Breadth-first: Process all of one level before visiting the next level.
    * Depth first: Process all the descendants of one child before processing
      all of the descendants of another child.
* Preorder: Process parent before children.
* Postorder: Process children before parent.
* Inorder (only depth first, usually binary): Process parent between
  children.
* Left-to-right vs. right-to-left (obvious)
* Most strategies implemented with a queue (breadth first), a stack
  (depth first), or recursion (depth first).

Binary Search Trees
-------------------

Binary search trees have special properties.  There is a total
ordering on the values in `N` which we will designate as
`<`.

* If `<p,0,c>` is in `child`, then `c < p`.
* If `<p,1,c>` is in `child`, then `p < c`.

We like binary search trees because we can find any value in O(height)
time.  If the tree is kept well balanced, that's O(logn), where n is the
number of values in the tree.

Balancing Binary Search Trees
-----------------------------

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

