---
title: Eboard 15  Pause for breath
number: 15
section: eboards
held: 2017-09-27
---
CSC 301.01, Class 15:  Pause for breath
=======================================

_Overview_

* Preliminaries
    * Notes and news
    * Upcoming work
    * Extra credit
    * Questions
* Insertion in 2-3 trees, revisited
* Deletion in 2-3 trees
* B-trees
* 2-3-4 trees vs. red-black trees

### News / Etc.

### Upcoming work

* [Exam 1](../exams/exam01) due TODAY at 5:00 p.m.
    * If you attend the Google talk at 4:00 p.m., you may have until
      7:00 p.m.
* [Assignment 5](../assignments/assignment05) due next Wednesday at 10:30 p.m.

### Extra credit (Academic)

* Google tech interview session, Today, 4:00-5:30 p.m., 3821
* Convocation, Thursday, 11am in JRC 101
* CS Table, Tuesday: Tapia

### Extra credit (Peer)

### Extra Credit (Misc)

### Other good things

* Women's soccer today at 4:30 p.m.
* Volleyball today at 7:00 p.m.

### Questions

Should the cover sheet be separate?
  : Yes.

What goes on the cover sheet?
  : Name
  : Number
  : Academic honesty statement 1
  : Signature and date for AHS 1
  : Academic honesty statement 2
  : Signature and date for AHS 2

What does a typical big-O proof look like?
  : You identify c and n0 and show why, for all n > n0,
    f(n) <= c*g(n).
  : Transitivity example (also in Skiena)
      * f(n) is in O(g(n)), g(n) is in O(h(n)).  Want f(n) is in O(h(n))
      * Because f(n) is in O(g(n)), there exist c1, n1 such that
        for all n > n1, f(n) <= c1*g(n). [Eqn1]
      * Because g(n) is in O(h(n)), there exist c2, n2 such that
        for all n > n2, g(n) <= c2*h(n). [Eqn2]
      * _Intuition: We want to use transitivity of <=._
      * For all n > n2, c1*g(n) <= c1*c2*h(n) [Eqn3]
        *Algebra: You can multiply both sides of an inequality by a
        positive number.)
      * _Intuition: We now have two equations that hold for only some
        n values.  We want to identify the subset of values for which
        both hold._
      * Let n0 be max(n1,n2).  Both Eqn1 and Eqn3 hold for all n > n0.
      * For all n > n0, f(n) <= c1*c2*h(n). (Transitivity of <=)
      * Let c be c1*c2.
      * Therefore, f(n) is in O(h(n))
    
How long is your solution to `bst-remove`?
  : 40 lines.  But I have three calls to `node`, each of which is
    four lines long.

Did you use a separate helper for `bst-remove` to find the appropriate replacement key/value?
  : No.  I just wrote a local helper.  It was five lines long.

For the hash function, should we really use 128.  You said "large prime".  128 is not prime as far as I know.
  : I misspoke.  alpha is the size of the alphabet.

Should I worry about `mod`?
  : If the computation is likely to overflow `int` or `long`, yes.
  : And yes, it will overflow
  : Note that if your computation is greater than INT_MAX / 128, it's
    time to `mod`.

Insertion in 2-3 trees, revisited
---------------------------------

Recall that our process for adding a value to a 2-3 tree is as follows:

* Follow the path to the appropriate position of the new value.
    * You should end up on the fringe of the tree.
* If there's room in the parent node, just add the value to the parent.
* If there's not room in the parent node, pretend to expand the node
  to three values and four children, then split the node at the center
  value and propagate the center value upward.

Visually

```
         +---+---+
         | x | z |
         +---+---+
        /    |    \
      nil   nil   nil

             |
             v

       +---+---+---+
       | x | y | z |
       +---+---+---+
      /    |   |    \
    nil   nil  nil  nil

             |
             v

           +---+
           | y |
           +---+
          /     \
       +---+   +---+
       | x |   | z |
       +---+   +---+
      /    |   |    \
    nil   nil  nil  nil
```

But what happens when we move the node up?  We may have the same
problem.  Without loss of generality, let's say that the node being
propagated up is on the right.

```
         +---+---+
         | p | r |
         +---+---+
        /    |    \
       T1   T2   +---+
                 | y |
                 +---+
                /     \
               T3     T4
```

All of `T1`, `T2`, `T3`, `T4`, are the same height.  This isn't quite
a 2-3 tree because the `y`-rooted subtree is too tall.  So we'll move up.

```
       +---+---+---+
       | p | r | y |
       +---+---+---+
      /    |   |    \
     T1   T2  T3    T4

             |
             v

           +---+
           | r |
           +---+
          /     \
       +---+   +---+
       | p |   | y |
       +---+   +---+
      /    |   |    \
     T1   T2  T3    T4
```

Note that because we end up with a lot of singleton nodes, subsequent
additions are likely to be much less costly.

Exercise
--------

_Build a 2-3 tree by successively adding a, c, e, g, i, h, f, d, b._

* Observations: It is hard to predict the structure in advance; it is
  affected by the order in which we add values.
* Observation: We tend to get singleton nodes scattered throughout the
  tree, which suggests that we won't propagate up all that much.

B-trees
-------

2-3 trees are a specialiation of "B-trees" - search trees in which you
have blocks of ordered keys, with links to subtrees in between.

What happens when your search tree doesn't fit into memory?  We will
need to read from disk.  That's awfully slow.

2-3-4 trees vs. red-black trees
-------------------------------

Deletion in 2-3 trees
---------------------

_Spend about five minutes thinking about how we delete from 2-3 trees.
Assume, as a starting point, that we only delete at leaves.  It will also
be helpful to think about the structure of the parents and the siblings._

