---
title: Eboard 34  Dynamic programming (1)
number: 34
section: eboards
held: 2017-11-17
---
CSC 301.01, Class 34:  Dynamic programming (1)
==============================================

_Overview_

* Preliminaries
    * Notes and news
    * Upcoming work
    * Extra credit
    * Questions
* Network flows wrapup
* Bipartite matching
* Motivating problem - Choosing stamps
* The value of caching
* Dynamic programming, generalized

### News / Etc.

### Upcoming work

* [Exam 2](../exams/exam02) due TONIGHT at 4:00 p.m. (or 5:00 p.m.)
* Read Skiena the rest of Skiena 6, unless you've done so already.
* My plan is to grade exam 2 and finish grading exam 1 over the weekend.
* "There's not a lot of time, how will I improve my grade if I'm not
  doing as well as I think I should be."
    * We'll figure something out.

### Extra Credit (Academic/Artistic)

### Extra credit (Peer)

* Pub-Free Quiz (after Turkey break?)
* Swim and dive meet, Saturday

### Extra Credit (Misc)

* Orchestra Saturday at 2pm

### Other good things

* "The First Time I Walked on the Moon".  Thursday 7:30, Friday 7:30,
  Saturday 2:00, Saturday 7:30, Sunday 2:00.
* Voice recitals Friday at 4:15 (Henderson) and 7:00 (Manuel)
* Jingle Bell Holidays in Grinnell tonight
* Singers and Oratorio Sunday at 2pm

### Questions

Network flows wrapup
--------------------

Sample graph

* S->A: 4
* A->B: 3
* B->T: 8
* S->C: 5
* C->D: 7
* D->T: 3
* D->B: 2
* C->A: 6

```
    A --> B
 4/ ^  3  ^ \ 8
 /  |     |  \
S   |6    |2  T
 \  |     |  /
 5\ |     | / 3
    C --->D
      8
```

Assumption: All edge weights are non-negative and finite.

Incorrect (but potentially instructive) algorithm

* For each edge, we will keep track of how much capacity we've used so far 
  and how much capacity remains.
* Repeat
   * In the graph of remaining capacity, find a path from s to t.
   * Find the smallest remaining capacity along that path.
   * Update usage on every edge by that amount.

Example of problem: Suppose the first path we find is SCABT.  We can
no longer run any data through SA.

Solution?

* Topological sort.  Nope, sorry, we haven't decided that this is acyclic.
* Add back edges.  Every time you move forward along an edge, you decrease
  the remaining capacity of that edge and increase the remaining capacity
  of the back edge.

Bipartite matching
------------------

Inputs:

* Two independent sets (e.g., "workers" and "tasks").
* A relationship between the sets (e.g., "worker 1 can do task 2 or
  3", "worker 2 can do task 1, 2, or 4", ...)

Output:

* A maximal set of pairs (one from set one, one from set two) that meets the
  relationships; each element can appear in at most one set.

Solution?

* Find the task with the minimum number of workers.  Choose the worker
  among those who has the fewest remaining tasks.  (In case of a tie,
  choose randomly.) [Sam thinks this is incorrect.]
* Use a graph.
     * A vertex for each worker; a vertex for each task.
     * Edge between a worker and each task the worker can do.
     * Add a start vertex linked to each worker.
     * Add an end vertex linked from each task.
     * Find max flow
* New algorithm design strategy: Model the problem as a graph and use
  a known graph algorithm.

The stamps problem
------------------

Input: Set of integers (e.g., 1, 2, 7, 15, 25) + another integer (t).
The set represents valid "stamp prices" (coin denominations, etc.), the
remaining integer represents postage cost for a letter (change to make).

Goal: Find the smallest set of integers whose sum = t.  You may 
repeat any integer.

Example: 14

* Bad answer 1 + 1 + 1 + 1 + 1 + 1 + 1 + 1 + 1 + 1 + 1 + 1 + 1 + 1 + 1 + 1 
* Best answer 7 + 7

Another example: 23: 15, 7, and 1

_How would you approach this problem?_

* Greed (always take the largest remaining stamp value)
* Divide and conquer (solve the problem for t/2 and double the solution,  
  or a variant thereof).
* Convert to a graph problem.
* Exhaustive search (find every set of stamps (how?) and take the smallest one.

Using the obvious greedy algorithm, find the number of stamps necessary
to make 21 cents , 37 cents

* Greedy for 21: 15, 2, 2, 2 (four stamps)
    * Optimal for 21: 7, 7, 7
* Greedy for 37: 25 (12 remaining), 7 (5 remaining), 2 (3 remaining), 2
  (1 remaining), 1 (0 remaining): Five stamps
    * Optima; 15, 15, 7
 
To solve minstamps(prices,value) - find minumum number of stamps (not
their values)

```
  estimate = infinite
  For each price in prices
    if (price < value)
      guess = minstamps(prices, value-price)
      if (guess+1 < estimate)
        estimate = guess+1
  return estimate
```

Slow but correct.

Monday: Turn it into fast but correct.

The value of caching
--------------------

Dynamic programming, generalized
--------------------------------

