Other Strategies for Sorting
----------------------------

If we don't sort by comparing values to each other, what other options
are there?  That is, what tools do you have?

* Decomposing the values (strings into letters, integers into bits)
* More memory! (Hopefully O(n))
* Divide and conquer?
* ...

Bucket Sort
-----------

Suppose we only have integers between 0 and 100.  What might we do?

It appears you've all thought about bucket sort.

What if our things may be different, but equal?  (E.g., we could be
sorting faculty by their easiness rating on RateMyProfessors.)

Is bucket sort stable?

Skienna tells us that sorting is always in Omega(nlogn).  So how does
it seem that we have an O(n) algorithm?

Radix Sort
----------

What if we have a large number of 32-bit unsigned integers?  We don't
want to use a table of size 2^32, so what are our other options?

It turns out we can reorder them according to their bits.  First we'll
do the lower order bit, then the next lower-order bit, then the next
lower-order bit, and so on and so forth

We'll do three bit radix sort as an example.

Is radix sort really an O(n) algorithm?
