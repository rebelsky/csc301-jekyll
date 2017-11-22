---
title: Eboard 36  Discussion of exam 2
number: 36
section: eboards
held: 2017-11-22
current: true
---
CSC 301.01, Class 36:  Discussion of exam 2
===========================================

_Overview_

* Preliminaries
    * Notes and news
    * Upcoming work
    * Extra credit
    * Questions
* Revisiting the cost of the stamps problem
* The 0-1 knapsack problem, continued
* Exam 2: Issues with problem 2 (Tries)
* Exam 2: Issues with problem 3 (Loop invariants)

### News / Etc.

* Have a good Thanksgiving.
* Warning! Weinman will be visiting class after Turkey break.

### Upcoming work

* [Homework 9](../assignment09) due Wednesday.
* Only one more homework after that one!  (Dynamic programming.)

### Extra Credit (Academic/Artistic)

### Extra credit (Peer)

### Extra Credit (Misc)

* Forum: A Community Responds — A Bias/Hate Incident Raising Issues of Free Speech and Inclusivity.  Tuesday, 11 a.m., Sebring-Lewis.

### Other good things

* Have a good Thanksgiving.

### Questions

Revisiting the cost of the stamps problem
-----------------------------------------



The 0-1 knapsack problem, continued
-----------------------------------

Problem: Given a list of (weight,value) pairs and a maximum weight,
find the subset of those pairs whose total weight is less than or 
equal to the maximum weight and whose total value is maximized.

Solution: Exhaustive search.

Issue: Exhaustive search is expensive.

Idea: Use dynamic programming.

Issue: While we could have a simple table for the stamps problem, we
somehow need to keep track of not just the weight remaining in the 
backpack, but also the remaining items.

Insight: 

Issues with problem 2 (Tries)
-----------------------------

We will consider some common issues so that you avoid them in the
future.

Code does not match GNU style.  

* Style improves readability
* Here's what I expect.
    * Two spacae indent
    * Braces on lines by themselves, indented (Sam likes comments on end 
      braces)
    * Type of procedure and procedure name on separate lines
    * Spaces after procedure names

```
int
trie_add (TrieNode *trie, char *str)
{
  if (NULL == trie)
    return 0;
  while (str[0])
    {
      ...
    } // while
} // trie_add
```

Violates levels of abstraction

* Examples
    * When the string to be deleted is not in the trie, prints an
      error message (or exits the program).
    * When the string to be added is already in the trie, prints an
      error message (or exits the program).
    * When the prefix is not in the trie, prints an error message.
* Notes
    * The user communicates with the UI (and vice versa)
    * The UI communicates with your utility code.
    * Don't work around that implicit barrier
* So
    * Utility code should not print error messages.
    * Utility code should not crash the program.
* But
    * If you must print something, print to `stderr`.

Memory leaks

* Common issues
    * Does not free the trie when done.
    * Does not free allocated strings.
* Note: You should be using some profiler (I use `valgrind`, CC
  recommends Address Sanitizer) to determine memory usage.
    * <http://www.cs.grinnell.edu/~weinman/courses/CSC161/2017F/modules/lists/labs/pointers-malloc.shtml>
* But how do I build the string as I go?
    * Feel free to allocate it, but free after you use it.
    * Allocate on the stack.  (Make it a local variable.)
    * Pass along something big enough to expand.

Other `malloc` issues

* `malloc` may fail.  You should check the return value.
* `malloc` does not zero out memory.  Hence, if you are allocating a
  node and expect to be able to check for null pointers in the children,
  you must initialize them to null.

Bad smells

* Magic numbers
* Code that is not DRY  (Don't Repeat Yourself)
     * (Constrast with WET?  Why Express Twice?)
* `for (i = 0; i < strlen (str); i++)`

Issues with problem 3 (Loop invariants)
---------------------------------------

A loop invariant

* Says something about the state of the system.
* Holds at the end of each iteration of the loop (if it holds at the
  beginning of each iteration).
* Is not the loop termination condition.
* Says something *useful* about the state of the system.
    * Loop termination + invariant => conclude postconditions

For this problem

* "There are at least two classes" is not a loop invariant, since
  it doesn't always hold at the end.
* "There is at least one class" is not a loop invariant, since it is
  effectively the loop termination condition.  (And tells us
  nothing useful.)
* "The number of humanities classes plus the number of social science
  classes equals the total number of classes" is not a useful loop
  invariant.

A solution

* Let S be the original number of social science classes and s be the
  current number of social science classes.
* s%2 == S%2

