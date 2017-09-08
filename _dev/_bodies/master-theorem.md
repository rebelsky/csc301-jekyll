Detour: Recursion vs. iteration
-------------------------------

* Many programmers worry about the hidden costs associated with recursion,
  such as locality and the cost of building the stack 
    * There's also a potential for stack overflow.
* Are there recursive procedures you've seen converted to iterative
  procedures?
* Can you convert every recursive procedure to an interative procedure?
* Are there general principles you can use to decide when you can convert
  a recursive procedure to an iterative procedure without a stack?
* Exercise: Divide-and-conquer exponentiation.

Recursion trees, revisited
--------------------------

* It sometimes helps to draw a tree that shows what's happening with the
  recursion.
* We show the size of the problem at each level.
* We can sum across each level, and then sum those sums to get an
  overall estimate of the running time.
* This analysis requires that we identify the sum of the values at each
  level and the number of levels.

Exercises

* Build the recursion tree for `T(n) = 2*T(n/2) + cn`._
* Build the recursion tree for `T(n) = 2*T(n/2) + c`._
* Build the recursion tree for `T(n) = 2*T(n/2) + n^2`._
* Build the recursion tree for `T(n) = 3*T(n/2) + c`._

Solving recurrence relations with the substitution method
---------------------------------------------------------

* Basically, this is proof by induction.
* We'll assume that the recurrence relation holds for values smaller than *n* 
  and then prove it for *n*.
* Unfortunately, it turns out that there are a lot of subtleties with
  this technique.
* _Exercise: Prove that if `T(n) = 2*T(n/2) + O(n)` and `T(n) = 1`, then
  `T(n) is in O(nlogn)`.

Solving recurrence relations with the Master Theorem
----------------------------------------------------

* The master theorem works for recurrences of the form
  `T(n) = aT(n/b)+f(n)`.
* The computation depends on the relationship between _f(n)_ and
  how quickly the `n/b` drops to 0.
* There are three rules
    1. If `f(n)` is in `O(n^(log_b(a)-e))` for some `e` > 0, then
    `T(n)` is in `Theta(n^(log_b(a)))`
    2. If `f(n)` is in `Theta(n^log_b(a))`, then
    `T(n)` is in `Theta(n^(log_b(a)*log(n)))`
    3. If `f(n)` is in `Omega(n^(log_b(a)+e))`_ for some `e` > 0, and
    `af(n/b) <= cf(n)` for some `c` < 1 and large enough `n`, 
    then `T(n)` is in `Theta(f(n))`.
* There's a simpler version (which I'm taking from Weiss).  This is
  for recurrences of the form `T(n) = aT(n/b) + O(n^k)`
* There are once again three rules
    1. If a > b^k, then T(n) is in O(n^(log_b(a)))
    2. If a = b^k, then T(n) is in O(n^(klog_2(n)))
    3. If a < b^k, then T(n) is in O(n^k)
* We'll try some basic examples.
