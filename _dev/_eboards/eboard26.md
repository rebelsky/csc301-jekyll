---
title: Eboard 26  Program verification (3)
number: 26
section: eboards
held: 2017-10-30
---
CSC 301.01, Class 26:  Program verification (3)
===============================================

_Overview_

* Preliminaries
    * Notes and news
    * Upcoming work
    * Extra credit
    * Questions
* Example - Efficient exponentiation with iteration
* Loop invariants, revisited
* Example - Dutch national flag
* Memory models, revisited

### News / Etc.

* Although grading was in the queue for the weekend, paperwork interfered.
* Do any of you consider yourselves competent Javascript programmers?

### Upcoming work

* Read Appendix B4 (Graphs) of CLRS for Wednesday.
* [Assignment 7](../assignments/assignment07) due Wednesday at 10:30 p.m.

### Extra credit (Academic/Artistic)

* CS Table, Tuesday at noon: The Google Memo
* Rebirth Brass Band, Wednesday at 7:30 p.m. in Herrick.
* CS Extras, Thursday at 4:15 p.m.: "Building your own programming language and other reasons to go to graduate school"

### Extra credit (Peer)

* RTS Friday at 9 p.m.
* Pub Quiz Wednesday at 9 p.m. in Bob's.
* VR club Sundays at 8pm.

### Extra Credit (Misc)

### Other good things

### Questions

What should heap sort do?  
  : Sort by putting into the heap and then taking out of the heap.
  : Split the array (conceptually) into two halves: heap part (at left)
    and the sorted part (at right)
  : Repeatedly grab largest remaining thing, swap it to the front of
    the sorted part (end of heap part), heap down from front, and
    continue.

How do I build a heap in place?
  : Split the array (conceptually) into heap and "random stuff"
  : When you "heap up" from the start of the random stuff, you've
    increased the size of the heap by 1 and decrased the amount of
    unprocessed stuff by 1.

How should we get the time?
  : Up to you.

Can we allocate an extra array for merge sort?
  : Yes.  Merge sort requires an extra array.

Do we need to remove it when we're done?
  : Yes.

Review - Efficient exponentiation with recursion
------------------------------------------------

Problem: Compute x^n % b in log(n) steps.

Hint: x^(2k) = (x^k)^2 = (x^2)^k.

```
int
powmod(int x, int n, int b)
{
  if (0 == n)
    {
      // x^0 == 1 for all nonzero x.
      return 1;
    }
  else if (n % 2 == 0)
    {
      // x^(2k) = (x^k)^2 = (x^2)^k.
      return powmod (x*x % b, n/2, b)
    }
  else
    {
      // x^n = x*x^n-1
      return (x*powmod(x, n-1, b)) % b;
    }
} // powmod
```

For the last case, can we do `(x*powmod(x*x % b, (n-1/2), b) % b`?
  : Yes, but it won't have a significant impact.

Example - Efficient exponentiation with iteration
-------------------------------------------------

Problem: Compute x^n % b in c*log(n) steps, iteratively.

```
int
powmod(int X, int N, int b)
{
  int x = X;
  int n = N;
  int stuff = 1;
  // Invariant: (stuff * x^n) % b == (X^N % b)
  while (n > 0)
    {
      if (0 == n % 2)
        {
          // stuff*(x*x)^(n/2) = stuff*x^n = X^N
          x = x*x;
          n = n/2;
          // xnew = x*x, nnew = n/2, ...
        }
      else
        {
          n = n-1;
          stuff = stuff*x;
          // stuffnew * x^(nnew) = (stuff*x)*x^(n-1) = stuff*x^n = X^N
       }
    } // while
  // (stuff * x^n) % b == (X^N % b) AND n == 0
  // (stuff * x^0) % b == (X^N % b) 
  // (stuff % b == (X^N % b) 
  return stuff % b;
} // powmod
```

Example - Dutch national flag
-----------------------------

Problem: Given an array of values (which we will red, white, and blue) in no 
particular order, reorder them so that the red values come before the white
and the white come before the blue.

### Preliminary code

Scaffolding in [examples/dnf](../examples/dnf).

```
enum color (RED, WHITE, BLUE);
typedef enum color color;

void
dnf (color flag[])
{
 ...
} // dnf
```

### Invariant (pictoral)

See whiteboard.

### Code

### Application
