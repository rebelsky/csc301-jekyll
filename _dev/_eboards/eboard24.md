---
title: Eboard 24  Program verification (2)
number: 24
section: eboards
held: 2017-10-25
current: true
---
CSC 301.01, Class 24:  Program verification (2)
===============================================

_Overview_

* Preliminaries
    * Notes and news
    * Upcoming work
    * Extra credit
* Goals for this unit
* Verifying imperative code
* Example - binary search
* Example - binary search, revised
* Verifying recursive procedures
* Additional topics (if time)
    * Example - Efficient exponentiation with recursion
    * Example - Efficient exponentiation with iteration
    * Loop invariants, revisited [if time]
    * Example - Dutch national flag [if time]

### News / Etc.

### Upcoming work

* [Assignment 6](../assignments/assignment06) due TONIGHT at 10:30 p.m.
* [Assignment 7](../assignments/assignment07) due next Wednesday at 
  10:30 p.m.

### Extra credit (Academic)

* _Saving Brinton_, Talk at 2pm TODAY in Harris.
* _Saving Brinton_, Wednesday at 7pm TODAY in the Strand.
* Gates Lecture, TONIGHT at 7:00 p.m. in JRC 101.  
* Convocation Thursday (11 am in JRC 101).
* Strange Escape Room Challenge.
* Protest BOT workshop, Friday 4pm in Burling 1st.  

### Extra credit (Peer)

* Scarlet and Black Swim and Dive Meeting Saturday.  (One hour suffices.)

### Extra Credit (Misc)

### Other good things

* Grinnell Singers Sunday at 2pm.

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
 4. loop
 5.   { MustBe(L,U) }
 6.   if L>U then
 7.     { L>U and MustBE(L,U) }
 8.     { T is not in the array }
 9.     P := 0; break
      else
10.     { MustBe(L,U) and L<=U }
11.     M := (L+U) div 2
12.     { MustBe(L,U) and L<=M<=U }
13.     case
14.       X[M] < T:
15.         { MustBe(L,U) and CantBe(1,M) }
16.         { MustBe(M+1,U) }
17.         L := M+1
18.         { MustBe(L,U) }
19.       X[M] = T:
20.       { MustBe(L,U) and X[M] = T }
21.         P := M; break
22.       X[M] > T:
23.         { MustBe(L,U) and CantBe(M,N) }
24.         { MustBe(L,M-1) }
25.         U := M-1
26.         { MustBe(L,U) }
        end case
27.   { MustBe(L,U) }
    end if
28. end loop
```

Example - binary search, revised
--------------------------------

_Write an O(logn) binary search that finds the *first* instance of a value 
in an array._  (Note that because it's O(logn), you can't just find an
instance and then look left.)

Verifying recursive procedures
------------------------------

Example - Efficient exponentiation with recursion
-------------------------------------------------

Example - Efficient exponentiation with iteration
-------------------------------------------------

Loop invariants, revisited
--------------------------

Example - Dutch national flag
-----------------------------

