---
title: Eboard 24  Program verification (2)
number: 24
section: eboards
held: 2017-10-25
---
CSC 301.01, Class 24:  Program verification (2)
===============================================

_Overview_

* Preliminaries
    * Notes and news
    * Upcoming work
    * Extra credit
* Goals for this unit
* Verifying imperative code
* Example - binary search
* Example - binary search, revised
* Verifying recursive procedures
* Additional topics (if time)
    * Example - Efficient exponentiation with recursion
    * Example - Efficient exponentiation with iteration
    * Loop invariants, revisited [if time]
    * Example - Dutch national flag [if time]

### News / Etc.

### Upcoming work

* [Assignment 6](../assignments/assignment06) due TONIGHT at 10:30 p.m.
* [Assignment 7](../assignments/assignment07) due next Wednesday at 
  10:30 p.m.

### Extra credit (Academic)

* _Saving Brinton_, Talk at 2pm TODAY in Harris.
* _Saving Brinton_, Wednesday at 7pm TODAY in the Strand.
* Gates Lecture, TONIGHT at 7:00 p.m. in JRC 101.  
* Convocation Thursday (11 am in JRC 101).
* Strange Escape Room Challenge.
* Protest BOT workshop, Friday 4pm in Burling 1st.  

### Extra credit (Peer)

* Scarlet and Black Swim and Dive Meeting Saturday.  (One hour suffices.)
* Tailgate for football team Saturday at 11:30 a.m. on the grassy knoll.
* German movie in Strand 4pm Sunday.

### Extra Credit (Misc)

### Other good things

* Support the football team on Saturday.
* Grinnell Singers Sunday at 2pm.

Goals for this unit
-------------------

* Think about / practice a common technique for "proving" that a program
  or algorithm is correct. 
* Practice thinking about the "state" of an imperative program.
    * Values associated with local variables (and parameters).
    * Values associated with global variables.
    * The "stuff" on the stack.
    * The "stuff" on the heap.
* Use program verification techniques to improve your algorithm design.

Verifying imperative code
-------------------------

* Annotate the code with information about appropriate parts of the
  state of the system.
     * Ideally, you have state info after every instruction
       (or set of related instructions).
* It should be provable that an instruction brings you from one state
  to the next state.
* Simplest instruction: assignment statement.
        ```
        {...} // may include "x = ?"
        x = 5;
        {... - "x = ?" + "x = 5"}

* Tests
        ```
        {S0}
        if TEST
          {S0 and TEST}
          consequent
          {S1}
        else
          {S0 and (not TEST)} 
          alternate
          {S2}
        end
        {S1 or S2} or {S1 intersect S2}
        ```

* Loops: Traditionally we both look at the state and put limitations
  on the state.  ("Loop invariants.")  A loop invariant is (a) a useful
  statement about the state of the system that (b) we know is true
  when we enter loop, (c) we know is true at the end of the body
     * Invariants plus "loop termination argument" go hand in hand
     * You can then guarantee that the invariant holds at the end of
       the loop.
  
* Function calls
    ```
    {S}
    call(f)
    {postconditions of f + things we know that f did not affect}
    ```

Detour fun with C

```
printf ("%d", x); // 5
foo(y);
printf ("%d", x); // 6
```

What are some ways that a call that does not seem to involve `x` modifies
`x`?

* `y` is a pointer to `x`.
* `x` is a global.
* Some other global contains a pointer to `x`.
* Someone wrote beyond the bounds of an array.
* ...

Verification is harder with pointers and with globals.  More system
state information is necessary.

Example - binary search
-----------------------

Here's a slightly modified version of Bentley's Figure 1.  We'll walk 
through it together.

```
Procedure: Binary search
Input: X, array of size N
Input: N
Input: T, a value (target)
Output: P, which is the index of T if T is in the array, and 0 o/w.
 1. { MustBe(1,N) }
    { This means that if X is anywhere in the array, it is between
      indices 1 and N, inclusive }
 2. L := 1; U := N
 3. { MustBE(L,U) }
    { Note: We know that L is 1 and U is N, but we're not including
      them in the statement about the state because it's not relevant. }
    { However, because we know those two things, we know the MustBe. }
    { This is also the loop invariant. }
 4. loop
 5.   { MustBe(L,U) }
 6.   if L>U then
 7.     { L>U and MustBE(L,U) }
 8.     { T is not in the array }
 9.     P := 0; break
      else
10.     { MustBe(L,U) and L<=U }
11.     M := (L+U) div 2
12.     { MustBe(L,U) and L<=M<=U }
13.     case
14.       X[M] < T:
15.         { MustBe(L,U) and CantBe(1,M) and L<=M<=U }
16.         { MustBe(M+1,U) }
17.         L := M+1
18.         { MustBe(L,U) }
19.       X[M] = T:
20.       { MustBe(L,U) and X[M] = T }
21.         P := M; break
22.       X[M] > T:
23.         { MustBe(L,U) and CantBe(M,N) }
24.         { MustBe(L,M-1) }
25.         U := M-1
26.         { MustBe(L,U) }
        end case
27.   { MustBe(L,U) }
    end if
28. end loop
```

Note: A proof would also involve ensuring that the loop terminates.
We should argue that U-L shrinks at every iteration.

Example - binary search, revised
--------------------------------

_Write an O(logn) binary search that finds the *first* instance of a value 
in an array._  (Note that because it's O(logn), you can't just find an
instance and then look left.)

Verifying recursive procedures
------------------------------

Trust the magic recursion fairy + good preconditions/postconditions.

You can also do nice proofs by induction.

Example - Efficient exponentiation with recursion
-------------------------------------------------

Example - Efficient exponentiation with iteration
-------------------------------------------------

Loop invariants, revisited
--------------------------

Example - Dutch national flag
-----------------------------

