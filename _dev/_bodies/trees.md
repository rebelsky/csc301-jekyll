Hash Tables: Semi-Formal Analysis
---------------------------------

* Proving that a hash function distributes values well is hard.  Every
  hash function will have some sets of values for which it does poorly.
* One trick: If we have some randomization in our choice of good
  hash functions, we can argue that we are unlikely to get one that
  distributes our current input badly.
* So, given a good hash function, a probed hash table, and a requiremnt
  that the hash table is no more than half full, what can we say?
* Half the time, we'll find an empty spot.   So 1/2 of the values take
  1 step.
* In the other half, we rehash.  Half the time, we'll find an empty spot.
  So 1/2 of the values take 2 steps
* In the other half, we rehash.  Half the time, we'll find an empty spot.
  So 1/4 of the values take 3 steps.
* In the other half, we rehash,
* So 1*1/2 + 2*1/4 + 3*1/8 + 4*1/16 + 5 *1/32 + 6*/64 + ....

Hash Functions and Hash Tables: Other Applications
--------------------------------------------------

* What did you think about the examples from Skiena?

Trees
-----

* What's a tree?
* What orders can we process the values in a tree?

Balancing Trees
---------------

* How might you balance an unbalanced tree?
