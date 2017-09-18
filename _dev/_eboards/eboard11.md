---
title: Eboard 11  Binary search trees
number: 11
section: eboards
held: 2017-09-18
current: true
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

Trees, introduced
-----------------

_Talk with your group about the following questions._

Is "Tree" an ADT or a Data Structure?  Both?  Neither?

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

Arity

Leaf

Parent

Child

Subtree

Path

Depth (of node)

Height (of tree)

Level

Descendent

Forest

Ancestor

Complete tree

Binary trees
------------

Traversing trees
----------------

There are approximately eight standard orderings for traversing trees.
What are they?

Binary search trees
-------------------

What are they?

Building balanced BSTs
----------------------

Suppose you have an arry of key/value pairs and want to build a balanced
binary tree from them.

Balancing BSTs.
---------------

