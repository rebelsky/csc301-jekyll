Proving Closed Forms of Recurrence Relations with Induction
-----------------------------------------------------------

* Basically, this is proof by induction.
* We'll assume that the recurrence relation holds for values smaller than *n* 
  and then prove it for *n*.
* Unfortunately, it turns out that there are a lot of subtleties with
  this technique, subtleties best learned through practice.
* _Exercise: Prove that if `T(n) = 2*T(n/2) + O(n)` and `T(n) = 1`, then
  `T(n) is in O(nlogn)`.

Randomized kth-Largest
----------------------

* How do you find the kth largest element of an *unsorted* array 
  (as quickly as possible)?
* Take about five minutes to brainstorm approaches.
* We'll then talk about techniques.
