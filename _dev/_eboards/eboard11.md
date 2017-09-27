---
title: Eboard 11  Binary search trees
number: 11
section: eboards
held: 2017-09-18
---
CSC 301.01, Class 11:  Binary search trees
==========================================

_Overview_

* Preliminaries
    * Notes and news
    * Upcoming work
    * Extra credit
    * Questions
* Tree basics & terminology
* Trees, formalized
* Binary trees
* Traversing trees
* Binary search trees
* Building balanced BSTs.
* Balancing BSTs.

### News / Etc.

* As seems to be the norm, my weekend failed to produce as much work time
  as I needed, and work took longer.  I remain behind on grading.
* We'll be discussing Red/Black trees on Wednesday and Friday.

### Upcoming work

* [Assignment 4](../assignments/assignment04), due 10:30 p.m. Wednesday
    * Implement hash tables in Scheme.
    * Reflect on how to implement sets.
* Exam 1 to be distributed Wednesday.

### Extra credit (Academic)

* CS Table, Tuesday, Hacktivism
* CS Extras, Thursday, 4:15 p.m., 3821, Study Abroad in CS
* One of the Happy Kareoke Fun Time activities
    * Musical, Friday 9pm, Gardner.
    * Workshop: Burn your fear.  Saturday, 2pm.  The Wall.
      Email [improv] to sign up.
    * Workshop: Creating through improv.  Sunday, 2pm.  The Wall.
      Email [improv] to sign up.
    * Musical, Sunday, 7pm, Gardner

### Extra credit (Peer)

### Extra Credit (Misc)

### Questions

How do I expand the hash table?

```
(define hash-table-new
  (lambda ()
    (vector 'hash-table (make-vector 100 null) ...)))

(define hash-table-expand
  (lambda (table)
    (let ([new-contents (make-vector (+ 1 (* 2 (hash-table-size table))))])
      ... ; copy the elements
      (vector-set! table 1 new-contents))))
```

Are there limitations to what can be in the key?
  : Any ASCII strings are valid.  But you have `char->integer` in Scheme.
  : So there are 128 different characters.
  : Remember: The hash function should give you a number between 0 and
    infinity.  You decide where to place it by mod'ing by the hash table
    size.

Trees, introduced
-----------------

_Talk with your group about the following questions._

Is "Tree" an ADT or a Data Structure?  Both?  Neither?

* ADT: Because data structures are things you directly implement.
* Data structure: There is a natural implementation: Nodes with pointers.

Detour: List is an ADT (we are organizing elements for iteration
and support the following operations: ...).  LinkedList or ArrayList
is a Data Structure (each element has a link to the next; the elements
are stored in an array)

It's complex.  A Tree is a way of organizing info, which may be more abstract
than ADT.  But we think of trees as "Nodes with pointers" which makes them
pretty concrete.  And we use them to implement other ADTs (e.g., "We implement
dictionaries with binary search trees.")

Note: We also represent binary trees as arrays with the understanding that
the children of the value at position i are at positions 2i+1 and 2i+2.
What are the central key operations?

Trees, formalized
-----------------

### Basic definition

We will denote "a tree of values of type X" as Tree<X>.

* If x is an X, Leaf(x) is a Tree<X>
* If x is an X and T1 ... Tn are all Tree<X>s, then so is
  Node(x,T1,T2,...,Tn).

### Empty leaves

We will denote "a tree of values of type X" as Tree<X>.

* Leaf is a Tree<X>
* If x is an X and T1 ... Tn are all Tree<X>s, then so is
  Node(x,T1,T2,...,Tn).

### Values only at leaves

* If x is an X, Leaf(x) is a Tree<X>
* If T1 ... Tn are all Tree<X>s, then so is Node(T1,T2,...,Tn).

Terminology
-----------

_Are there any of these terms that you don't know?_

Binary trees

Root

Node

Arity of a node is the number of children that node has.  In a binary
tree, internal nodes have arity 1 or 2 and leaves have arity 0.

Leaf

Parent

Child

Subtree

Path

Depth (of node)

Height (of tree)

Level

Ancestor - Generalization of parent

Descendent - Generalization of child.  It's a property. ("a is a 
descendent of "b).  (For all a s.t. a is a descendent of b ...)

* A child of x is a descendent of x.
* If y is a descendent of x, then every child of y is also a descendent
  of x.

Forest - A collection of trees

Complete tree - All internal nodes have all children. 

BSTs
----

Binary search tree (BST) is a tree (usually binary) of values 
(or key/value pairs) with the property that

* The keys of all the nodes in the left subtree are less than the key
  of the root.
* The keys of all the nodes in the right subtree are greater than the key
  of the root.
* The same property applies for all subtrees.

If we are using BSTs to implement dictionaries, each key appears only
once.

If you have BSTs in which a value can appear multiple times, you can make
one or both of the orderings not-strict.

Detour: Why BSTs?
-----------------

Given that a balanced BST is still O(logn) for add and find, while a
hash table is expected amortized O(1), why would I use BSTs rather than
hash tables to implement dictionaries?

* They look pretty.
* Professors like to make students work with pointer structures.
* We want to think in terms of orderings.
    * For iteration or segmenting.
* Because there is no natural hash function.

Traversing trees
----------------

There are approximately eight standard orderings for traversing trees.
What are they?

* Choice one: Recursively (depth-first) or across levels (breadth-first)
* Choice two: left-to-right or right-to-left
* Choice three for breadth-first: bottom-up or top down
* Choice three for depth-first: When do I look at the root value

How would you implement breadth-first, left-to-right, top-down traversal?

* We put nodes in a queue
* We repeatedly grab the front of the queue, process it, and add its
  children to the queue.

We can use a stack to do depth-first.

Building balanced BSTs
----------------------

Suppose you have an array of key/value pairs and want to build a balanced
binary tree from them.

Option one: After each insert, observe where it's not balanced and reorganize.

Option two: Sort the key/value pairs.  The middle one is the root.
Recursively build the left and right halves.

Balancing BSTs
--------------

Think about this for next class: How do you keep your binary search trees
balanced?  (You don't need them perfectly balanced; you just need to keep
the depth O(logn))

* Approach one: Shift around nodes when it's bad.
* Approach two: Reorganize
