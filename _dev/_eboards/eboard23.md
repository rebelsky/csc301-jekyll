---
title: Eboard 23  Program verification (1)
number: 23
section: eboards
held: 2017-10-23
---
CSC 301.01, Class 23:  Program verification (1)
===============================================

_Overview_

* Preliminaries
    * Notes and news
    * Upcoming work
    * Extra credit
    * Questions
* Skip lists
* Goals for this unit
* Verifying imperative code
* Example - binary search
* Example - binary search, revised

### News / Etc.

* I hope you had a wonderful fall break.
* I was less efficient in grading than I had hoped.  You get snacks
  instead of exams.  Sorry.
* The topic for this week is new to CSC 301 for this year and is part
  of a broader reorganization of the CS curriculum.

### Upcoming work

* [Assignment 6](../assignments/assignment06) due Wednesday at 10:30 p.m.
* For Wednesday's class, Read PM on program correctness
  <http://www.cs.grinnell.edu/~osera/courses/csc207/17fa/readings/02-correctness.pdf>

### Extra credit (Academic)

* _They Call Me Q_, Tonight at 7:00 p.m. in Harris Concert Hall.
* MASSS talk on text analysis with R Tuesday at 11 a.m. somewhere in Math.
* _Saving Brinton_, Wednesday at 7pm in the Strand.
* Gates Lecture, Wednesday at 7:00 p.m. in JRC 101.  Professor Sylvester Johnson, Director of the Humanities, Virginia Tech, talk will examine the twentieth-century roots of contemporary national security responses targeting American Muslims as state enemies. 
* Convocation Thursday (11 am in JRC 101).
* Protest BOT workshop, Friday 4pm in Burling 1st.  
    > Bots are small automated programs that index websites, edit Wikipedia entries, spam users, scrape data from pages, launch denial of service attacks, and other assorted activities, both mundane and nefarious. On Twitter bots are mostly spam, but occasionally, they’re creative endeavors.  Mark Sample will lead participants in the creation of bots that can "reveal the injustice and inequality of the world and imagine alternatives. ... that question how, when, who and why."

### Extra credit (Peer)

### Extra Credit (Misc)

### Other good things

Skip lists
----------

_I will take your questions and then add my own questions for you._

Goals for this unit
-------------------

Verifying imperative code
-------------------------

Example - binary search
-----------------------

Here's a slightly modified version of Bentley's Figure 1.  We'll walk 
through it together.

```
 1. { MustBe(1,N) }
 2. L := 1; U := N
 3. { MustBE(L,U) }
 5.   { MustBe(L,U) }
 4. loop
 6.   if L>U then
 7.     { L>U and MustBE(L,U) }
 8.     { T is not in the array }
 9.     P := 0; break
      end if
10.   { MustBe(L,U) and L<=U }
11.   M := (L+U) div 2
12.   { MustBe(L,U) and L<=M<=U }
13.   case
14.     X[M] < T:
15.       { MustBe(L,U) and CantBe(1,M) }
16.       { MustBe(M+1,U) }
17.       L := M+1
18.       { MustBe(L,U) }
19.     X[M] = T:
20.       { MustBe(L,U) and X[M] = T }
21.       P := M; break
22.     X[M] > T:
23.       { MustBe(L,U) and CantBe(M,N) }
24.       { MustBe(L,M-1) }
25.       U := M-1
26.       { MustBe(L,U) }
      end case
27.   { MustBe(L,U) }
28. end loop
```

Example - binary search, revised
--------------------------------

_Write an O(logn) binary search that finds the *first* instance of a value 
in an array._  (Note that because it's O(logn), you can't just find an
instance and then look left.)

