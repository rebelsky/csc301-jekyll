---
title: "Assignment 7: Sorting out sorting"
link: true
assigned:
due: 2017-11-01
due-time: 10:30pm
---
# {{ page.title }}

*Due*: {{ page.due | date: '%A, %-d %B %Y' }} by {{ page.due-time }}

*Summary*: In this assignment, you will use techniques of program
verification to produce verifiably correct implementations of
merge sort.  To reflect on the relationships between sorting algorithms.

*Purpose*: To continue your practice implementing sorting algorithms.
To provide you with experience with formal methods.

*Collaboration* (code): You may discuss this assignment with anyone you
like, provided you credit such discussion when you submit the assignment.
You will learn more if you do most of the coding on your own, but you
may choose to submit the code for the assignment as a pair or trio.

*Submitting* (code): Create a tarball from your code and then mail it
to your course instructor with a subject of **CSC 301 Assignment {{
page.number }} (Your Name)**.  You should, of course, substitute your
name in that subject.

*Evaluation*: We will primarily evaluate your work on its *correctness*
(e.g., does it compute what it is supposed to; does it meet the
requirements of the assignment); *clarity* (e.g., is it easy to read,
is it well formatted and documented); and *efficiency* (e.g., does it
achieve its goal quickly and with limited resources).  These criteria
will be modified, as appropriate, for written and coding assignments.

*Warning*: So that this assignment is a learning experience for everyone,
we may spend class time publicly critiquing your work.

In considering sorting algorithms that they have implemented, programmers 
should worry about at least three issues.

* How do I know that my code is correct?
* Is my code as efficient as it can be?
* Should I be using a more efficient sorting algorithm?

In this assignment, you will explore these three issues in more depth.

1. In C, implement a recursive merge sort algorithm for arrays
of integers.  

    Show that your code is correct by annotating it using a level of detail
    similar to that Bentley uses in his Figure 1 binary search.

2. In C, implement an iterative merge sort algorithm for arrays of
integers.  The iterative merge sort algorithm first merges neighboring
elements into pairs, then neighboring pairs into four-tuples, then
four-tuples into octuples, and so on and so forth.

    Show that your code is correct by annotating it using a level of detail
    similar to that Bentley uses in his Figure 1 binary search.

3. You should have implemented heap sort in Scheme for a previous assignment.
Reimplement heap sort in C.

    Show that your code is correct by annotating it using a level of detail
    similar to that Bentley uses in his Figure 1 binary search.


4. All of these are O(nlogn) algorithms.  But how do they behave in terms
of constant multiplier?  Write a program that generates an appropriate
range of inputs and determines which algorithm seems best in practice.
Include both your program and the output in your tarball.

   For example, you might repeatedly generate random arrays of size 10000, 
   20000, 40000, and 80000 elements and time each sorting algorithm using
   those arrays.  (Your numbers may vary.  On some systems, these sizes
   will be too small for meaningful timing.  On others, these sizes will
   be too large for the program to run within a reasonable amount of time.)
   You might also think about nearly sorted arrays, arrays that are 
   "backwards" and other cases.

