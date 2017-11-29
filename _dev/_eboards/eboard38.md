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
* [Homework 10](../assignments/assignment10) due next Wednesday.
* Final is in-class on the morning of Wednesday, December 13.

### Extra Credit (Academic/Artistic)

* CS Extras Thursday: Anya's Advisor.

### Extra credit (Peer)

* Swim meet this coming weekend.
* Chamber Ensembles Saturday at 4:00 p.m.
* One Acts this weekend.

### Extra Credit (Misc)

* Mental Health Campus Resource Fair.  Friday at 4pm in JRC 209.

### Other good things

* Jazz Ensemble Concert Friday at 7:30 p.m.
* YGB Saturday at 2:00 p.m.
* Collegium Concert Sunday at 2:00 p.m.
* Festival of trees at Drake Friday afternoon

### Questions

Approximate substring matching
------------------------------

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

### Variant one

_How would you update the algorithm to accommodate *substring* matching
rather than whole string matching?  (E.g., to figure out the best place
to align `"habit"` in `"alphabetical"`?)_

### Variant two

Exact substring matching
------------------------

The brute-force approach
------------------------

```
for (s = 0; s < length(source) - length(target), s++)
  {
    for (i = 0; i < length(target) && source[s+i] == target[i]; i++)
      ;
    if (i == length(target)
      return s;
  } // for s
return -1;      // Not found
```

Review: The hash-code approach
------------------------------

