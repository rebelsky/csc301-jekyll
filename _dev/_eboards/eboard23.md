---
title: Eboard 23  Skip lists (was Program verification (1))
number: 23
section: eboards
held: 2017-10-23
---
CSC 301.01, Class 23:  Skip lists (was Program verification (1))
===============================================

_Overview_

* Preliminaries
    * Notes and news
    * Upcoming work
    * Extra credit
    * Questions
* Skip lists
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

What should we do about maxlevel?
  : Option 1: Pick some number, like 20.
  : Option 2: Expand the dummy node at the front when you build a node
    of a level higher than maxlevel.
  : In either case, you should probably start the dummy node at a relatively
    large height.

What should we do if the key is not in the list (for search or delete).
  : Up to you, as long as it's documented.
  : In Java, traditionally throw an exception.
  : In C, return null.
  : Have a separate `containskey` method which is a precondition.

Should the number of incoming pointers equal the number of outgoing pointers
(except for the dummy node at the front and the nil node at the end)?
  : Yes.

How would you print figure 1e?
  : As follows

```
X X X X
| | | |
3 | | |
| | | |
6 6 6 6
| | | |
7 | | |
| | | |
9 9 | |
| | | |
```

Are you printing keys or values?
  : Keys.  That's all we really care about right now.  If you'd like, you
    could also print the values.

```
X X X X
| | | |
X | | |         3: Some value
| | | |
X X X X         6: Another value
| | | |
X | | |         7: And another
| | | |
X X | |         9: And yet another
| | | |
```

What are the big ideas in skip lists?  What purpose do they serve?  How
are they implemented?
  : Skip lists are designed to allow you to search quickly through a
    collection of values.  They implement Dictionaries.  They are
    expected O(logn) for find, remove, and insert.
  : It's like a linked list, but you have extra pointers that skip some
    of the nodes.  By using the extra pointers, we can quickly skip
    over large chunks of the list.

Given that we have tries and hash tables, why bother with skip lists?
  : Probably easier to implement than balanced binary trees.
  : May use less memory than Tries.
  : Avoids the evil rehashing that sometimes happens in hash tables.
  : Doesn't rely on a well designed hash function or a good distribution
    of data.  It works for any (orderable) data.
  : Iteration from smallest to largest is easy.  (Just follow the links
    at level 0.)  So for instances in which we need that capability, 
    superior to hash tables.
  : Works with values not easily decomposable into sequences.
  : Reveals new ways of thinking about data structure design.

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

