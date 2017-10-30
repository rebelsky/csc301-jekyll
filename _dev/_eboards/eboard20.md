---
title: Eboard 20  Discussion of exam 1
number: 20
section: eboards
held: 2017-10-08
---
CSC 301.01, Class 20:  Discussion of exam 1
===========================================

_Overview_

* Preliminaries
    * Notes and news
    * Upcoming work
    * Extra credit
    * Questions
* Problem 2
* Problem 4
* Problem 5
* Problem 3
* Problem 1
* Problems with Problem 1

### News / Etc.

* Quick mid-semester survey.
    * I focus on "talk about a problem in small groups, then as a large group", but we also have other possible approaches, some of which we've used.
        * [1] The current approach is working well.
        * [2] Sam should talk less; let us present our results.
        * [3] Less small group work, lecture more (eboard).
        * [4] Less small group work, lecture more (white board).
        * [5] Less small group work, lecture more (and use slides).
    * Other than getting grading done, what is something that I can do to improve the class?
* Welcome back to those who were gone last week.

### Upcoming work

* [Assignment 6](../assignments/assignment06) due Wednesday after
  break at 10:30 p.m.

### Extra credit (Academic/Artistic)

* CS Table Tuesday, GHC
* CS Alumni Tuesday at 4:15 p.m.
* CS Extras Thursday, ???
* Aspen Trio, 7:30 p.m., Wednesday, S-L.

### Extra credit (Peer)

* MASSS tomorrow.  11 a.m.  Euler's Totient Function
* Alterntive Spring Break, 6-8pm, Tuesday JRC 227

### Extra Credit (Misc)

### Other good things

* Volleyball vs. Beloit, Tuesday night at 7:00 p.m..

### Questions

Problem 2
---------

_This one was difficult enough that I gave everyone full credit if they
made a reasonable attempt._

Problem 4
---------

4a. Your goal was to explain the variant of the Gauss formula in this one,
not just to invoke the Gauss formula.

4b. Proofs by inducation require explicit statement of the inductive
hypothesis.

4c. I'm sorry.

Problem 5
---------

See handout.

Remove an element from a tree, thereby building a new tree.

* Case A: Empty tree
    * Done.  Return the empty tree.
* Case B: String matches the root of the tree (subtree)
    * Subcase 1: No left subtree: Return right
    * Subcase 2: No right subtree: Return left
    * Subcase 3: No subtree/leaf: Covered by previous two cases
    * Subcase 4: Nonempty left subtree, Nonempty right subtree
* Case C: String is less than the root
    * Build a new tree by removing string from the left
* Case C: String is greater than the root
    * Build a new tree by removing string from the right

Problem 3
---------

These seemed mostly straightforward, as long as you know how to follow
the language of proof.

* By the definition of Big-Oh, I know that there exist c and n0 s.t., ...
* Let m be ....  Let d be ....
* [Some algebra]
* We have shown that for all n > m, q(n) <= d*r(n).
* Therefore, q(n) is in r(n)
* Q.E.D.

Example question

* if h(n) is in O(g(n) + f(n))
* and f(n) is in O(g(n))
* then h(n) is in O(g(n))

Note: We're doing this to show that a common technique is legal.  E.g.,
we say O(n^2 + n) is the same as O(n).

Proof

1. Because h(n) is in O(g(n) + f(n)), there exist n1 and c1, s.t.,
   h(n) <= c1*(g(n) + f(n)) for all n > n1. [Definition of Big-O]
2. Becaues f(n) is in O(g(n)), there exist n2 and c2, s.t
   f(n) <= c2*g(n) for all n > n2. [Definition of Big-O]
3. h(n) <= c1*g(n) + c1*f(n) for all n > n1
4. h(n) <= c1*g(n) + c1*c2*g(n) for all n > n1, n > n2 [2,3,algebra]
5. h(n) <= (c1+c1*c2)*g(n) for all n > n1, n > n2 [4,algebra]
6. Let n0 be max (n1,n2), let c be c1 + c1*c2. [...]
7. h(n) <= c*g(n) for all n>n0 [5,6,algebra]
8. h(n) is in O(g(n)). [def'n]

Problem 1
---------

See handout.

Some issues ...

* Used `pow`.  If you're working with integers, use integers.  floats
  do not always translate in the way you think.  C's coercion can 
  give you an off-by-one (or more) error.
* The computation could overflow.  You have a responsibility to
  regularly `mod` by some upper bound.
* Assumed that the two hash values matching meant that you'd found
  the substring

Problems with Problem 1
-----------------------

And then there's the big problem ....

* Some of the solutions I saw looked incredibly like either (a) code easily
  available on the Interweb or (b) CLRS.  Many cited neither.
* Why would students make this choice, given that I said that you could
  use things from the Interweb provided you cited?
* What should I do (other than spend time thinking about the issue and
  how to talk about it in class)?

