---
title: Assignment 3
number: 3
link: true
assigned:
due: 2017-09-13
due-time: 10:30pm
current: true
---
# {{ page.title }}

*Due*: {{ page.due | date: '%A, %-d %B %Y' }} by {{ page.due-time }}

*Summary*: In this assignment, you will explore some issues related
to divide-and-conquer algorithms and asymptotic analysis.

*Purpose*: To enhance your understanding of divide-and-conquer 
algorithms.  To give you practice with the master theorem and proof
by induction.

*Collaboration* (code): You may discuss this assignment with anyone you
like, provided you credit such discussion when you submit the assignment.
You will learn more if you do most of the coding on your own, but you
may choose to submit the code for the assignment as a pair or trio.

*Collaboration* (written): You may discuss this assignment with anyone you
like, provided you credit such discussion when you submit the assignment.
You will find that you learn the material better more if you follow 
initial design discussions in a group with individual writing.  Each 
person should write up his, her, zir, or their own work and submit it
individually.

*Submitting* (code): Create a tarball from your code and instructions for
running code.  Mail the tarball to your course instructor with a subject
of **CSC 301 Assignment {{ page.number }} (Your Name)**.  You should,
of course, substitute your name in that subject.

*Submitting* (written): Turn in your work under my office door.  While I
would prefer that you use LaTeX, you may certainly do your work by hand.
Make sure to include your name, course information, and date at the
top of the page.  If you use paper torn from a loose-leaf notebook,
make sure to remove or trim any lose edges.

*Evaluation*: We will primarily evaluate your work on its *correctness*
(e.g., does it compute what it is supposed to; does it meet the
requirements of the assignment); *clarity* (e.g., is it easy to read,
is it well formatted and documented); and *efficiency* (e.g., does it
achieve its goal quickly and with limited resources).  These criteria
will be modified, as appropriate, for written and coding assignments.

*Warning*: So that this assignment is a learning experience for everyone,
we may spend class time publicly critiquing your work.

## Part 1: The kth-largest algorithm

1. Look up the randomized kth-largest divide-and-conquer algorithm. This
algorithm find the _k_th largest element of an array of numbers by repeatedly
partitioning the array and then recursing on one of the two partititions.

2. Implement the simpler `median` procedure and try your solution on
HackerRank at <https://www.hackerrank.com/challenges/find-the-median>.

3. You will be implementing the generalized algorithm in C.  Write a
fairly comprehensive set of unit tests.

4. Implement the algorithm in C.

5. Write a program that assesses the number of steps your algorithm takes
by repeatedly running it on randomly generated arrays.  You may, of course,
have to extend the original algorithm to log procedure calls or number of
times through a loop.

## Part 2: Exploring recursive bounds

Find bounds for each of the following by using the master theorem.

* a. `T(n)` <= `3T(n/3) + c*n^2`.
* b. `T(n)` <= `3T(n/3) + c*n`.
* c. `T(n)` <= `3T(n/3) + c`.
* d. `T(n)` <= `3T(n/5) + c*n^2`.
* e. `T(n)` <= `3T(n/5) + c*n`.
* f. `T(n)` <= `3T(n/5) + c)`.
* g. `T(n)` <= `9T(n/3) + c*n^2)`.
* h. `T(n)` <= `9T(n/3) + c*n)`.
* i. `T(n)` <= `9T(n/3) + c`.
* j. `T(n)` <= `T(2n/3) + c*n^2)`.
* k. `T(n)` <= `T(2n/3) + c*n`.
* l. `T(n)` <= `T(2n/3) + c`.

## Part 3: Verifying results.

Prove the bounds of a-c using induction on n.

