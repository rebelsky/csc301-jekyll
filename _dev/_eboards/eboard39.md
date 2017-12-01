---
title: Eboard 39  Improved string-matching algorithms
number: 39
section: eboards
held: 2017-12-01
current: true
---
CSC 301.01, Class 39:  Improved string-matching algorithms
==========================================================

_Overview_

* Preliminaries
    * Notes and news
    * Upcoming work
    * Extra credit
    * Questions
* Quick review
* The hash-code approach
* Keeping track of look-ahead
* Building the table

### News / Etc.

* Warning! Our Chair is visiting class this week.
* Cut/Close/Balance period finishes on Friday at 5:00 p.m.
    * You may start Add/Drop on Monday the 4th.

### Upcoming work

* [Homework 10](../assignments/assignment10) due next Wednesday.

### Extra Credit (Academic/Artistic)

* **NEW** CS Table Tuesday: Exotic PLs

### Extra credit (Peer)

* Swim meet this coming weekend.
* Chamber Ensembles Saturday at 4:00 p.m.
* One Acts this weekend.

### Extra Credit (Misc)

* Mental Health Campus Resource Fair.  Friday at 4pm in JRC 209.
* **NEW** Newtown film on Tueday.

### Other good things

* Festival of trees at Drake THIS afternoon
* Jazz Ensemble Concert TONIGHT at 7:30 p.m.
* YGB Saturday at 2:00 p.m.
* Collegium Concert Sunday at 2:00 p.m.

### Questions

Quick review
------------

Our goal: Given a *source* of length n and a *target* of length m, find the 
first (or all) matches of the source in the target.

Approach one: Try every position.

* Correct.
* Potentially inefficient.  O(nm)

The hash-code approach
----------------------

_a.k.a. the Rabin Karp algorithm_

* Write a hash function that is easy to update
    * Constant time to compute hash(t[i+1...i+n]) from
      hash(t[i..i+n-1]) and t[n].
* Compute the hash code of the source.
* Compute each hash code in the target.
* If any match ...

_What's the typical hash function?_

_Why might Sam think this is not an O(n+m) algorithm?_

_Why might Sam be wrong?_

Keeping track of look-ahead
---------------------------

Let us return to the original (try matching at position 0, then at position
1, then at position 2, ...).

Suppose our source is `aaab` and our input is `aaaa___`.  What should we
do upon seeing that the `b` and the fourth `a` don't match?  In particular,
do we really have to look at t[1] and t[2]?

### The magic table

#### Example 1

* pattern: a a a b
* target: a a a a a c a a a a a a b

#### Example 2

* pattern: a b a b a c
* target: a b a b a b a c

### Using the table (algorithm)

```
Inputs:
  target, a string
  source, a string
  P, the table described above
Steps:     
  i = 0; // Index into target
  j = 0; // Index into source
  while (i < length(target) - length(source))
    if (j == length(source))
      return MATCH at i-j.
    else if (target[i] == source[j])
      ++i;
      ++j;
    else if j == 0
      ++i
    else
      j = P[j]
```

Building the table
------------------

How would you start?
