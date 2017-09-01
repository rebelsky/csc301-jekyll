Formalizing the problem
-----------------------

Given

* A set of named "locations" (nodes), N
* A set of costs of getting between locations, E
    * E is an element of (NxN) => Z
* A starting point, s in N
* An ending point, t in N

Find a sequence of points, n_a_0, n_a_1, ... n_a_k, such that
    
* n_a_0 = s
* n_a_k - t
* sum(E(n_a_j,n_a_(j+1))) is minimized 
    * That is, for all sequences n_b_0, n_b_1, ... n_b_l,
      in which n_b_0 is s and n_b_l is t.
      sum(E(n_a_j,n_a_(j+1))) &lt;= sum(E(n_b_i,n_b_(i+1)))

Selecting possible approaches
-----------------------------

_Talk to your group for a minute.  Be prepared to present two or
three ways we might start approaching the problem._

Some sample solutions
---------------------

_I will assign approaches to groups.  Groups will have five minutes
to think about them and then present._

Analyzing the sample solutions
------------------------------

_We will then think about each._

A hint
------

_What if we wanted the shortest path from s to *every* node._

A more standard solution
------------------------
