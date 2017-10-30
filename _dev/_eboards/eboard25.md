---
title: Eboard 25  Program verification (3)
number: 25
section: eboards
held: 2017-10-27
---
CSC 301.01, Class 25:  Program verification (3)
===============================================

_Overview_

* Preliminaries
    * Notes and news
    * Upcoming work
    * Extra credit
    * Friday PSA
    * Questions
* Example - binary search, revised
* Example - Efficient exponentiation with recursion
* Example - Efficient exponentiation with iteration
* Example - Dutch national flag

### News / Etc.

* A pair of requests.
     * Should be easy: Treat people with respect
     * Harder: Even when they don't treat you with respect
* A useful read: <https://www.nytimes.com/2017/10/23/opinion/engaging-fanatics.html>
* Grading is in the queue for the weekend!

### Upcoming work

* Read Appendix B4 (Graphs) of CLRS for Monday.
* [Assignment 7](../assignments/assignment07) due Wednesday at 10:30 p.m.

### Extra credit (Academic/Artistic)

* Protest Bot workshop, Friday 4pm in Burling 1st.  
* Rebirth Brass Band Wednesday 7:30 p.m. in Herrick.

### Extra credit (Peer)

* Scarlet and Black Swim and Dive Meeting Saturday 9am-1pm.  
  (One hour suffices.)
* Tailgate Saturday on the Grassy Knoll.

### Extra Credit (Misc)

### Other good things

* Grinnell Singers Sunday at 2pm.
* American Football Saturday.
* European (and beyond) Football Saturday.

### Friday PSA

### Questions

Do you realize that Scheme and C are different languages?
  : Yes.  Sorry.  It will be easy or good or both for you to implement 
    heaps in C.

Example - binary search, revised
--------------------------------

Goal: Find the *first* instance of T in A.  In logarithmic time.
* So some Slight modifications.  

Statement:

* Input: A, a *zero-based* sorted array of integers
* Input: N, the number of elements in the array.  (Can be 0.)
* Input: T, an integer (target value)
* Output: P, an integer
    * If T appears in A, then (a) A[P] == T and
      *(b) If P > 0, A[P-1] < T.*
    * If T does not appear in A, then P == -1.
* Language: *C-like*
* Also: Does not modify A, N, T, or anything outside of the procedure.

Approach: Keep track of a range of interest using L and U.

Questions for you to talk about, then we'll do the problem together.

* Termination condition(s).
    * Abstractly: We've found the position or determined that T is not
      in the array.
    * L >= U
* Loop invariant.
    * In the old algorithm, MustBe(L,U) meant that *if T appears in A*, then
      T is between index L and index U.
    * In the new algorithm, MustBe(L,U) could mean that *if T appears in A*, 
      then THE FIRST INSTANCE T is between index L and index U.
    * In the new algorithm, MustBe(L,U) could mean that *if T appears in A*, 
      then is between index L and index U AND T does not appear between
      index 0 and L-1.
* How do you know that the range shrinks?

```
int
newbinsearch (int A[], int N, int T)
{
  // Note: MustBe(I,J) means (a) if T appears in A, then it appears
  // in A[I]..A[J] and (b) T does not appear in A[0..I-1].

  // MustBe(0,N-1)
  int L := 0;
  int U := N-1;
  // MustBe(L,U) AND L >= 0
  // "Size" for termination: U-L
  while (L < U)
    { 
      // MustBe(L,U) AND L >= 0 AND L < U
      int M = (L + U) / 2;      // Rounds down.  Assume no overflow.
      // MustBe(L,U) and 0 <= L <= M < U
      if (A[M] >= T)
        {
          // MustBe(L,U) and 0 <= L <= M < U and CantBe(M+1,N)
          // Modified CantBe: THe first instance cant be in that range
          // MustBe(L,M) and 0 <= L ...
          U = M
          // MustBe(L,U) and L >= 0
          // Termination argument: Since M < U, U-L is smaller
        }
      else
        {
          // MustBe(L,U) and 0 <= L <= M < U and A[M] < T, CantBe(0,M)
          // MustBe(M+1,U) and L >= 0 and ...
          L = M+1
          // MustBe(L,U) and L >= 0
          // Termination argument: Since M+1 > L, U-L is smaller
        }

      // MustBe(L,U) and L >= 0
    } // while
  // MustBe(L,U) AND (L >= U) AND (L >= 0)
  if (L == U) && A[L] == T
    // A[L] = T, A[L-1] != T, Therefore L is the index of the first
    // appearance.
    return L;
  else
    // (MustBe(L,U) and L>U) => T is not the array
    // (MustBe(L,U) and L==U and A[L] != T) => T is not array
    // T is not in the array
    return -1;
} // newbinsearch
```

The following is correct, but inappropriate, code that Sam started to
write.

```
      if (A[M] > T)
        {
          // MustBe(L,U) and 0 <= L <= M < U and CantBe(M,N-1)
          // See Bentley for CantBe
          // MustBe(L,M-1) and 0 <= L ...
          U = M-1
          // MustBe(L,U) and L >= 0
        }
```

Example - Efficient exponentiation with recursion
-------------------------------------------------

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
     // Hint: x^(2k) = (x^k)^2 = (x^2)^k.
     return powmod (x*2 % b, n/2, b)
   }
 else
   {
     // x^n = x*x^n-1
     return x*powmod(x, n-1, b) % b;
   }
} // powmod
```

Example - Efficient exponentiation with iteration
-------------------------------------------------

Problem: Compute x^n % b in log(n) steps, iteratively.

Example - Dutch national flag
-----------------------------

Problem: Given an array of values (which we will red, white, and blue) in no 
particular order, reorder them so that the red values come before the white
and the white come before the blue.
