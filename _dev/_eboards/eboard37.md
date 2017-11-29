---
title: Eboard 37  Dynamic programming (3)
number: 37
section: eboards
held: 2017-11-27
current: true
---
CSC 301.01, Class 37:  Dynamic programming (3)
==============================================

_Overview_

* Preliminaries
    * Notes and news
    * Upcoming work
    * Extra credit
    * Questions
* Review: Core ideas of dynamic programming
* The edit distance problem
* Formulating a solution
* Varying the solution

### News / Etc.

* Warning! Our Chair is visiting class this week.
* I hope you had a great Turkey break.  I did not complete exam grading.
  (I think it's currently third in my work queue.)

### Upcoming work

* [Homework 9](../assignments/assignment09) due Wednesday.
* Only one more homework after that one!  (Dynamic programming.)
* Final is in-class.

### Extra Credit (Academic/Artistic)

* CS Table Tuesday (unknown topic)
* CS Extras Thursday (unknown topic)

### Extra credit (Peer)

* Swim meet this coming weekend.
* Chamber Ensembles Saturday at 4:00 p.m.
* Pub-free quiz

### Extra Credit (Misc)

* Forum: A Community Responds — A Bias/Hate Incident Raising Issues of Free Speech and Inclusivity.  Tuesday, 11 a.m., Sebring-Lewis.
* Mental Health Campus Resource Fair.  Friday at 4pm in JRC 209.

### Other good things

* Jazz Ensemble Concert Friday at 7:30 p.m.
* Collegium Concert Sunday at 2:00 p.m.

### Questions

Review: Core ideas of dynamic programming
-----------------------------------------

* Typically used for optimization problems (sometimes involving exhaustive
  search)
* Key idea: Build a table of intermediate results.
     * Need to design the table
     * Need to figure out the relationship of cells to other cells.
       (Recursive formulation of the solution.)
* Example: For 0-1 knapsack, the great idea was a two dimensional table,
  with cell (i,j) gives the best way to make weight of i with elements
  0...j. (approximately)
* Generally gives us algorithms that run in the size of the table.

The edit distance problem
-------------------------

* Input: 
   * Two strings (source and target) 
       * source has the form s[1] ... s[n].
       * target has the form t[1] ... t[m].
   * Three cost functions
       * Cost of deleting a character 
       * Cost of inserting a character 
       * Cost of replacing a character 
* Goal: Find a sequence of transformations that converts source
  to target with the minimum cost.
* Note: Each cost function is typically constant, but we could permit
  them to vary based on the character we are inserting or deleting or
  even the position of the character.

### An example

What's the best way to transform `abbababa` to `bbaababb` 

* Given that insertion, deletion, and replacement all cost 1.
* Given that deletion costs 1, insertion costs 2, and replacement costs 4.
    * Hint: Don't replace.

Strategy for the first one?

* Three replacements, cost of 3

Strategy for the second one

* Delete the first a gives bbababa, cost of 1
* Add an a after the second b, gives bbaababa, total cost of 3
* Delete last a, cost of 1, gives bbaabab, total cost of 4
* Add a b at the end, cost of 2, gives bbaababb, total cost of 6

Formulating a solution
----------------------

Dynamic programming suggests that we should

* Design a table.  (What goes in each cell, what does it represent?)
* Design a formula for filling in the cells of the table. (How do
  we compute a cell based on prior cells?)

So, let's try.

* Remember that our goal is to find the minimum edit distance from s
  to t.  (And, optionally, the operations we need for that edit
  distance.)

C[i,j] stands for minimum cost of converting s[0..i] to t[0..j].

i is a column, j is a row

Goal 0: Define column 0 and row 0

Goal 1: Define C[i,j] in terms of C[i',j'] where i'<i and/or j'<j

Note: Deletion costs `d`, Insertion costs `a`, replacement costs `r`

```
C[0,0] = 0
C[i,0] = d + C[i-1,0] (for i>0)
     * Permit C[i,0] = d(i,s[i]) + C[i-1,0]
     * You generally won't worry about cost functions, but it's useful
       to write formulate that accommodate them
C[0,j] = a + C[0,j-1] (for j>0)
C[i,j] = if (s[i] == t[j]) then
           min(d+C[i-1,j], C[i-1,j-1], a+C[i,j-1]) 
         else 
           min(d+C[i-1,j], r+C[i-1,j-1], a+C[i,j-1]) 
```

How long does this take to run?  O(mn).  Not great, but not bad.

Varying the problem 
-------------------

What if we just care about the best *position* of source within target?

