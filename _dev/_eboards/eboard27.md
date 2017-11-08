---
title: Eboard 27  Program verification (4)
number: 27
section: eboards
held: 2017-11-01
---
CSC 301.01, Class 27:  Program verification (4)
===============================================

_Overview_

* Preliminaries
    * Notes and news
    * Upcoming work
    * Extra credit
    * Questions
* Loop invariants, revisited
* Example - Dutch national flag

### News / Etc.

### Upcoming work

* [Assignment 7](../assignments/assignment07) due TONIGHT at 10:30 p.m.
* [Assignment 8](../assignments/assignment08) due next Wednesday at 10:30 p.m.
  (All written problems!)

### Extra credit (Academic/Artistic)

* Rebirth Brass Band, Wednesday at 7:30 p.m. in Herrick.
* Convocation, Thursday at 11:00 a.m. in JRC 101.  Some Econ thing.
* CS Extras, Thursday at 4:15 p.m.: "Building your own programming language and other reasons to go to graduate school"

### Extra credit (Peer)

* RTS Friday at 9 p.m.
* Pub Quiz TONIGHT at 9 p.m. in Bob's.
* VR club Sundays at 8pm in DLAB.

### Extra Credit (Misc)

### Other good things

### Questions

Loop invariants, revisited
--------------------------

* A technique for (a) verifying that programs with loops are correct and
  (b) developing programs that involve loops.
* Core idea: Have a statement about the state of the system that holds
  before each iteration of the loop.  It also holds at the end of each
  iteration.  It therefore holds when the loop terminates.  It is useful
  for showing that the loop achieved its goal.
* In addition, we need to show that the loop terminates.
* Three examples: 
    * Binary search ("if it's in the array, it's in this section.")
    * Modified binary search ("if the first appearance is in the array,
      it's in this section")
    * Exponentiation ("stuff*x^n = X^N")
* Sam's experience is that loop invariants help with loops that deal
  with arrays.  Those invariants are often pictorial.

Example - Dutch national flag
-----------------------------

Problem: Given an array of values (which we will call red, white, and
blue) in no particular order, reorder them so that the red values come
before the white and the white come before the blue.

Goal: In place, O(n)

Note: In practice, the red, white, and blue are predicates, rather
than values.  

Proportions are not known in advance.

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

* Four parts: processed reds, then processed whites, then unprocessed
  stuff then processed blues.
* R: For i in [0..p1), A[i] is red.
* W: For i in [p1..p2), A[i] is white
* B: For i in [p3..n), A[i] is blue
* For i in [p2..p3), A[i] is unknown
* Goal: Shrink the unknown section until it's gone

### Code

How do I set p1, p2, and p3 so that these important parts of the invariant hold?

```
int p1 = 0;
int p2 = 0;
int p3 = n;
```

We can stop when `p3 <= p2`; the unknown region is empty.

```
// R, W, B, p1 >= 0, p2 >= 0
while (p3 > p2)
  {
    // R, W, B, p1 >= 0, p2 >= 0, p3 > p2
    // R, W, B, p1 >= 0, p2 >= 0, p3 > 0
    if (WHITE == A[p2])
      {
        // R, B, A[p1..p2) is white
        // R, B, A[p1..p2+1) is white
        p2 += 1;
        // We've shrunk p3-p2
      } 
    else if (RED == A[p2])
      {
        // A[0..p1) is red, A[p1..p2) is white, B
        // Note: A[p1] is white (or maybe not???)
        swap(A,p1,p2)
        // A[0..p1+1) is red, A[p1+1..p2+1) is white
        p1 += 1;
        p2 += 1;
        // We've shrunk p3-p2;
      }
    else if (BLUE == A[p2])
      {
        swap(A, p2, p3);
        // R, W, B
        // We haven't changed the size.  Danger!  
      }
    // Option 1: A[p3-1] is blue.  This is safe.
    if (BLUE == A[p3-1])
      {
        // R, W, A[p3..n) is blue
        // R, W, A[p3-1..n) is blue
        p3 -= 1;
        // R, W, B
        // We've shrunk p3-p2
      } 
  } //
```
### Application
