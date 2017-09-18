---
title: Eboard 09  Hash Tables
number: 9
section: eboards
held: 2017-09-13
---
CSC 301.01, Class 09:  Hash Tables
==================================

_Overview_

* Preliminaries
    * Notes and news
    * Upcoming work
    * Extra credit
    * Questions
* Review of hash tables.
* Hash functions, revisited.
* Other uses of hash tables and hash functions.

### News / Etc.

* Today's class may be sketchier than normal because I lost thirty minutes
  of prep/reflection time due to fire alarms.

### Upcoming work

* [Assignment 3](../assignments/assignment03), due 10:30 p.m. TONIGHT
    * Code via email
    * Printed under door
* [Assignment 4](../assignments/assignment04), due 10:30 p.m. Next Wednesday
    * Implement hash tables in Scheme.
    * Reflect on how to implement sets.

### Extra credit (Academic)

* CS Extras, Thursday, Klinge Map Group on Cauldron
* CS Table, Tuesday, ???

### Extra credit (Peer)

_???_

### Extra Credit (Misc)

_???_

### Other good things

### Questions

Loop invariants help you a whole lot in writing partition correctly.  What
is a loop invariant.
  : It is a way of thinking about the state of the system.
  : Usually with arrays.
  : If the invariant holds at the start of one iteration of the loop,
    it still holds at the end of that iteration.
  : It provides useful information about what our loop accomplishes.

What should we track?
  : How about array references.

Can we assume that n is a power of whatever in the inductive proofs?
  : If you must.
  : But you could also try doing so without that assumption. 

What's the difference between strong and weak induction.
  : Weak: If it works for n-1, it should work for n
  : Strong: If it works for <= n-1, it should work for n

What do you want us to do for part b?
  : Figure out which of the three patterns is at play.  Explain why.
    Use that pattern.

Will you force us to argue regularity?
  : It would be nice, but no.

Review of hash tables
---------------------

_What are the key ideas of hash tables?_

* We have pairs of keys and values (dictionaries).  We want to look 
  up values by keys.
* We use a hash function that takes keys and returns an integer and use
  integer to index into an array where we store key/value pairs.
* It gives expected constant time lookup of values by keys.

_What are some design decisions we make in implementing hash tables?_

* Sometimes two keys end up with the same place in the array, particulary
  when we mod by the size of the array.
    * We can put a linked list at that point in the array (chaining/bucketing)
    * We can look in a nearby cell (probing)
* To keep the buckets small, we generally grow the underlying array when
  it reaches some percent of capacity.
* It is important to have a good  hash function, one that distributes
  keys fairly uniformly across the number space.
* The size of the underlying array may be important.

Hash functions, revisited
-------------------------

_What does the following hash function do?_

[Borrowed from Skienna p. 89]

    #define alpha SOME_LARGE_PRIME
    int hash(char *s)
    {
      int len = strlen(s);
      int code = 0;
      for (int i = 0; i < len; i++)
        {
          code += s[i] * expt(alpha, len-(i+1))
        } // for
      return code;
    } // hash

_Suppose we have a really long string.  What the difference between
`hash(substring(str, 0, k))` and `hash(substring(str, 1, k+1))`?
E.g., `hash(substring(str, 0, 6)` vs `hash(substring(str, 1, 7))`_

* subtract s0*alpha^5
* multiply by alpha
* add s6

Other uses of hash tables and hash functions
--------------------------------------------

_Ideas stolen from Skiena_

How could you use hash functions or tables to help you ...

* Detect plagiarism
* Determine if string `a` is a substring of string `b`?

