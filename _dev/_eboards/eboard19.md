---
title: Eboard 19  Radix sort
number: 19
section: eboards
held: 2017-10-06
---
CSC 301.01, Class 19:  Radix sort
=================================

_Overview_

* Preliminaries
    * Notes and news
    * Upcoming work
    * Extra credit
    * Questions
    * PSA
* Another sorting example
* Radix sort
* Analyzing radix sort
* Bucket sort, revisited
* Analyzing bucket sort

### News / Etc.

* Exam 1 to be returned Monday, for real.

### Upcoming work

* [Assignment 6](../assignments/assignment06) due Wednesday after
  break at 10:30 p.m.

### Extra credit (Academic)

* CS Table Tuesday, GHC
* CS Extras, Tuesday, Alums
* CS Extras Thursday, ???
* Nice Fish

### Extra credit (Peer)

* Neverland players (negative extra credit).
* Cool Art thingy Saturday 1-3 pm
* RTS tonight 9:30 in Loose Lounge

### Extra Credit (Misc)

* Any "successor to 10/10" event.

### Other good things

* Volleyball vs. Beloit, Friday at 7:00 p.m.
* Women's Tennis vs. St. Norbert, Saturday at 9:00 a.m.
* Volleyball vs. Lake Forest, Saturday at 1:00 p.m.
* Women's Tennis vs. Ripon, Saturday at 3:00 p.m.
* Football, Saturday at 1:00 p.m.

### Questions

Will you return our homework?
  : Maybe after break.

Another sorting example
-----------------------

* Cards set up with "slot" for 1 and a whole for zero.
* A is 00001, B is 00010, C is 00011, D is 00100, etc.
* I want to separate the first fifteen cards from the last eleven cards
  (or maybe sixteen/ten).  How can I do so easily?
* Can I use that capability to sort?  Let's see.
* Put all of the 0's in position 0 before all of the 1's in position 0.
* Put all of the 0's in position 1 before all of the 1's in position 1.
* Put all of the 0's in position 2 before all of the 1's in position 2.
* Put all of the 0's in position 3 before all of the 1's in position 3.
* Put all of the 0's in position 4 before all of the 1's in position 4.
* This appears to take five steps.
* As long as I can encode all my values in five bits, I can sort *any* number
  of elements in five steps.

Radix sort
----------

Given a collection of values represented in fix-width binary.  Binary order
is the same as th eorder of values.

* Start from the lower order bit and work toward upper order bit,
  putting things with a zero before things with a one.  (Preserving order
  within any bit value.)

Running time is O(n * #bits)

Why does it work?

After each round, the elements are sorted according to their last
k bits

After the first round, all the things with zero come before all the things
with 1 in the rightmost bit.  They are sorted by the rightmost bit.

After the second round, we have 00 before 01 before 10 before 11 because
we've preserved order within the lower bits..

Analyzing radix sort
--------------------

Is this stable?

* Yes

What happens if you go left to right instead of right to left?

* Nothing sensible that I know.

How do you sort in reverse?

* Put the zeros after the 1's

How much space does this use?  Big-O, exact?

* We can't use the Quicksort "swap from the ends" approach, because that
  breaks stability, and we need stability, for example, to make sure that
  the 00's come before the 01's.
* As far as I know, there's no way to do this in place for an array.

If we have a list, rather than an array, we can build two other lists,
one of the zeros and one of the ones.  We'll also have a pointer to the
end of each of those lists to make it easy to append.

Node *current;
Node *zeros;
Node *ones;
Node *lastzero;
Node *lastone;

```
while (current)
  {
    Node *next = current->next
    if (current->bitofinterest == 0)
      {
        last0->next = current;
        last0 = current;
        last0->next = null;
      }
    else
      {
        last1->next = current;
        last1 = current;
        last1->next = null;
      }
    current = next;
  }
last0->next = ones;
current = zeros;
```

For arrays, we probably need an array of size n/2.  O(n)

Bucket sort, revisited
----------------------

Analyzing bucket sort
---------------------

