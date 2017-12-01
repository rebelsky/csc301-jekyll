---
title: Eboard 38  Basics of string matching
number: 38
section: eboards
held: 2017-11-29
---
CSC 301.01, Class 38:  Basics of string matching
================================================

_Overview_

* Preliminaries
    * Notes and news
    * Upcoming work
    * Extra credit
    * Questions
* Approximate substring matching
* Exact substring matching
* The brute-force approach
* Review: The hash-code approach

### News / Etc.

* Warning! Our Chair is visiting class this week.
* Cut/Close/Balance period finishes on Friday at 5:00 p.m.
    * You may start Add/Drop on Monday the 4th.

### Upcoming work

* [Homework 9](../assignments/assignmen09) due tonight.
    * Please use the folder attached to my bulletin board.
* [Homework 10](../assignments/assignment10) due next Wednesday.
* Final is in-class on the morning of Wednesday, December 13.

### Extra Credit (Academic/Artistic)

* CS Extras Thursday: Anya's Advisor.

### Extra credit (Peer)

* Swim meet this coming weekend.
* Chamber Ensembles Saturday at 4:00 p.m.
* One Acts this weekend (Saturday at 8, Sunday at 2).

### Extra Credit (Misc)

* Mental Health Campus Resource Fair.  Friday at 4pm in JRC 209.

### Other good things

* Jazz Ensemble Concert Friday at 7:30 p.m.
* YGB Saturday at 2:00 p.m.
* Collegium Concert Sunday at 2:00 p.m.
* Festival of trees at Drake Friday afternoon

### Questions

What should we do on the tourist problem if an edge includes an invalid city?
  : The preconditions of the problem have been violated.

For the tourist problem, can we print as we go or do we have to wait until we've read all the input?
  : Whatever is easier.

Should we try it online?  
  : Sure.  Send me the results of your tests.  (Optional.)


Approximate substring matching: review
--------------------------------------

Reminder: We use dynamic programming to match strings.

```
          source
  C  "" s1 s2 s3 s4 ...
    +--+--+--+--+--+--
t ""|  |  |  |  |  | ...
a   +--+--+--+--+--+--
r t1|  |  |  |  |  | ...
g   +--+--+--+--+--+--
e t2|  |  |  |  |  | ...
t    .   .  .  .  .
```

Meaning: `C[i,j]` is the cost of converting `substring(source,i)`
to `substring(target,j)`.

### The algorithm

```
C[0,0] = 0
C[i,0] = d + C[i-1,0] (for i>0)
C[0,j] = a + C[0,j-1] (for j>0)
C[i,j] = if (s[i] == t[j]) then
           min(d+C[i-1,j], C[i-1,j-1], a+C[i,j-1]) 
         else 
           min(d+C[i-1,j], r+C[i-1,j-1], a+C[i,j-1]) 
```

```
          source
  C  "" s1 s2 s3 s4 ...
    +--+--+--+--+--+--
t ""| 0| d|2d|3d|4d| ...
a   +--+--+--+--+--+--
r t1| a|  |  |  |  | ...
g   +--+--+--+--+--+--
e t2|2a|  |  |  |  | ...
t    .   .  .  .  .
```

Note that we could also make `a`, `d`, and `r` functions of the
position and character.

Approximate substring matching: Additional issues
-------------------------------------------------

### Variant one

_How would you update the algorithm to accommodate *substring* matching
rather than whole string matching?  (E.g., to figure out the best place
to align `"habit"` in `"alphabetical"`?)_

A brute force strategy

* Build the table for source vs ""
* Build the table for source vs t[1]
* Build the table for source vs t[1..2]
* Build the table for source vs t[1..3]
* ...
* Build the table for source vs t[1..m]
* Build the table for source vs t[2]
* Build the table for source vs t[2..3]
* Build the table for source vs t[2..4]
* ...
* Build the table for source vs t[2..m]
* Build the table for source vs t[3]
* ...

This should work, in that it looks at every possible solution, but it's
*really* inefficient.

A better solution

* Column 0 is all 0's.  Represents "we don't care about leading characters"
* Minimize across the last column to find the cost of the best match.

### Variant two

_The whole string matching problem only gives us a cost.  How do
 we update the algorithm so that each cell includes both cost and
 steps to achieve that cost?  `S[i,j]` are the steps to achieve 
 `C[i,j]`._


```
C[0,0] = 0
S[0,0] = <>
C[i,0] = d + C[i-1,0] (for i>0)
S[i,0] = S[i-1,0] ++ <D.i>
C[0,j] = a + C[0,j-1] (for j>0)
S[0,j] = S[0, j-1] ++ <A.j>
C[i,j] = if (s[i] == t[j]) then
           min(d+C[i-1,j], C[i-1,j-1], a+C[i,j-1]) 
         else 
           min(d+C[i-1,j], r+C[i-1,j-1], a+C[i,j-1]) 
S[i,j] = if (C[i,j] == d+C[i-1,j])
           S[i-1,j] ++ <D.i>
         ...
```

Exact substring matching
------------------------

Approximate matching is hard.  Best algorithm is O(mn).  Exact substring 
matching is easier.

* Find the first instance of source in target.
* Find all instances of source in target.
* Find any instance of source in target.

The brute-force approach
------------------------

```
for (s = 0; s < length(target) - length(source), s++)
  {
    for (i = 0; i < length(source) && target[s+i] == source[i]; i++)
      ;
    if (i == length(source)
      return s;
  } // for s
return -1;      // Not found
```

_What is the asymptotic upper bound on the algorithm and what is an input
that reaches that upper bound?_

Worst case O(mn).

* source: `habit`
* target: `habihabihabihabihabihabihabihabihabihabihabihabihabihabihabihabihabihabihabihabihabihabihabihabit`.

A worse one

* source: `hhhhhhhhhhi`
* target: `hhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhhi`

Our question for next class: Can we do better than O(mn) and, if so, how?

Review: The hash-code approach
------------------------------

This doesn't solve our problem in general, although it does in most cases.
