---
title: Eboard 36  Discussion of exam 2
number: 36
section: eboards
held: 2017-11-22
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

* [Homework 9](../assignments/assignment09) due Wednesday.
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

When we talk about the running time, we talk about the size of the input.

* Our input is some stamp prices and a total price.
* The total price is n.
* We found an algorithm that is O(n).
* Is `n` really the size of the input?
    * No: We've ignored the stamp prices.  (We'll just ignore that
      issue.  The problem is now, "Stamp prices are p1,...,pk.  Given
      n, find the minimum number of stamps that make price n."
    * There are a constant number of stamps, which accommodates the
      "we check n-p1, n-p2, ..." issue.
    * The "size" of the input is the number of bits required to represent
      n.  So the size, s, is log_2(n).  This algorithm is an O(2^s)
      algorithm.
* This only becomes an issue when we start talking formally about P vs NP.
* Our algorithm is still O(n).  But it's not a deterministic algorithm whose
  runing time is a polynomial in the size of the input (informal def'n of P)

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

Insight: Two dimensional table.  The second dimension represents
"the subset of the original elements that contains only elements
0...i"

In each cell (after the first row), we populate each square with the
"better" of 

* a: the same column, previous row, which represents "Don't take item i"
* b: column c-w, previous row, which represents "Take item i and then
  fill the rest of the backpack"
    * i is the row
    * c is the column number (the intermediate weight we are solving for)
    * w is the weight of item i

It should not matter we fill it horizontally or vertically, except
for data locality.

* Or, if we want an optimization, we only need to keep two rows around
  if we do it in row order.

The row is the number of items in the "prefix subset" of the original set.

Issues with problem 2 (Tries)
-----------------------------

We will consider some common issues so that you avoid them in the
future.

Code does not match GNU style.  

* Style improves readability
* Here's what I expect.
    * Two space indent
    * Braces on lines by themselves, indented (Sam likes comments on end 
      braces)
    * Type of procedure and procedure name on separate lines
    * Spaces after procedure names

```
TrieNode *
new_trie_node (void)
{
} // new_trie_node

/**
 * triad returns 1 if it successfully adds the string and 0 otherwise.
 */
int
trie_add (TrieNode *trie, char *str)
{
  if (NULL == trie)
    return 0;
  while (str[0])
    {
      ...
    } // while
  return 1;
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
        * `char *str = malloc (...);`
        * recursive-call
        * `free (str)`
    * Allocate on the stack.  (Make it a local variable.)
        * `char str[SIZE]`
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

