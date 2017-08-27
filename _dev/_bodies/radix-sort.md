Demo
----

* We will demo the magic Google sorting stick.
* We will consider how this works.
* I call this "Parallel Radix Sort"

Thining About Radix Sort
------------------------

* We did an informal description of radix sort on Friday.
* Questions:
    * What's the core idea?
    * Why does it work?
    * What's the running time?
    * How much extra space do you need?
    * How would you adapt radix sort to work with strings?

String Radix Sort
-----------------

* We'll need to pad all of the strings to the same length (or do some
  clever work to deal with those extra letters).

        for (i = maxlen-1; i >= 0; i--)
          for each string, str
            queues[str[i]].enqueue(str)
          end for
          merge the queues back into a list
        end for

Re-Costing Radix Sort
---------------------

* integer radix sort is O(32*n), more or less.  But is it really better
  than any of the O(nlogn) sorting algorithms?  After all, logn will
  almost certainly be less than 32.
* Will it help to look at it in terms of the string sorting algorithm?
* How much does it cost to compare two values?
