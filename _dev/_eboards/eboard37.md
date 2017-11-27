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

* [Homework 9](../assignment09) due Wednesday.
* Only one more homework after that one!  (Dynamic programming.)
* Final is in-class.

### Extra Credit (Academic/Artistic)

* CS Table Tuesday (unknown topic)
* CS Extras Thursday (unknown topic)

### Extra credit (Peer)

* Swim meet this coming weekend.
* Chamber Ensembles Sunday at 4:00 p.m.

### Extra Credit (Misc)

* Forum: A Community Responds — A Bias/Hate Incident Raising Issues of Free Speech and Inclusivity.  Tuesday, 11 a.m., Sebring-Lewis.
* Mental Health Campus Resource Fair.  Friday at 4pm in JRC 209.

### Other good things

* Jazz Ensemble Concert Friday at 7:30 p.m.
* Collegium Concert Sunday at 2:00 p.m.

### Questions

Review: Core ideas of dynamic programming
-----------------------------------------

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

Formulating a solution
----------------------

Dynamic programming suggests that we should

* Design a table.  (What goes in each cell?)
* Design a formula for filling in the cells of the table. (How do
  we compute a cell based on prior cells?)

Varying the problem 
-------------------

