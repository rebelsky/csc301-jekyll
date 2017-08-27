Recursion Trees, Revisited
--------------------------

* It sometimes helps to draw a tree that shows what's happening with the
  recursion.
* We show the size of the problem at each level.
* We can sum across each level, and then sum those sums to get an
  overall estimate of the running time.
* This analysis requires that we identify the sum of the values at each
  level and the number of levels.
* _Exercise: Build the recursion tree for `T(n) = 2*T(n/2) + cn`._
* _Exercise: Build the recursion tree for `T(n) = 2*T(n/2) + c`._

Solving Recurrence Relations with the Substitution Method
---------------------------------------------------------

* Basically, this is proof by induction.
* We'll assume that the recurrence relation holds for values smaller than *n* 
  and then prove it for *n*.
* Unfortunately, it turns out that there are a lot of subtleties with
  this technique.
* _Exercise: Prove that if `T(n) = 2*T(n/2) + O(n)` and `T(n) = 1`, then
  `T(n) is in O(nlogn)`.

Solving Recurrence Relations with the Master Theorem
----------------------------------------------------

* The master theorem works for recurrences of the form
  `T(n) = aT(n/b)+f(n)`.
* The computation depends on the relationship between _f(n)_ and
  how quickly the `n/b` drops to 0.
* There are three rules
    1. If `f(n)` is in `O(n^(log_b(a)-e))` for some `e` > 0, then
    `T(n)` is in `Theta(n^(log_b(a)))`
    2. If `f(n)` is in `Theta(n^log_b(a))`, then
    `T(n)` is in `Theta(n^(log_b(a)*log n))`
    3. If `f(n)` is in `Omega(n^(log_b(a)+e))`_ for some `e` > 0, and
    `af(n/b) <= cf(n)` for some `c` < 1 and large enough `n`, 
    then `T(n)` is in `Theta(f(n))`.
* There's a simpler version (which I'm taking from Weiss).  This is
  for recurrences of the form `T(n) = aT(n/b) + O(n^k)`
* There are once again three rules
    1. If a > b^k, then T(n) is in O(n^(log_b(a)))
    2. If a = b^k, then T(n) is in O(n^klog_2(n))
    3. If a < b^k, then T(n) is in O(n^k)
* We'll try some basic examples.

Randomized kth-Largest
----------------------

_If there's time, we'll go over this._
