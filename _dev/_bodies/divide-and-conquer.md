Divide and Conquer Algorithms
-----------------------------

* One of our favorite techniques.
* Divide into smaller problems.  Solve those problems.  Combine.
* A nice use of recursion.

Analyzing Divide-and-Conquer Algorithms
---------------------------------------

* Our normal mechanisms for asymptotic analysis do not work for 
  divide-and-conquer algorithms, which are typically recursive,
  rather than iterative.
* Because they are recursive, we tend to design recursive functions
  that express the running time.
* For example, for merge sort, our recurrence is

        T(1) = 1
        T(n) = 2*T(n/2) + theta(n)

* Why?  Because we do two recursive calls on size n/2 and then spend
  n extra work merging.

Estimating the Value of Recurrence Relations
--------------------------------------------

* So, how do we find out what function the recurrence relation
  provides.
* One strategy: we try to make a good guess and then prove it correct
  using induction.
* I find it easiest to make good guesses by working up from the base case
  or down from the broader recursive case.
* Working downward

        T(n) <= 2*T(n/2) + cn
             <= 2*(2*T(n/4) + c*n/2) + cn
             = 4*T(n/4) + 2*n
             <= 4(2*T(n/8) + c*n/4) + 2*n
             = 8*T(n/8) + 3*n
             ...

             <= (2^k)*T(n/(2^k)) + k*n

        Let k = log_2(n)

             <= n*T(1) + nlog_2(n).

* Working upward

        T(2) = 2*T(1) + 2c = 2 + 2c
        T(4) = 2*T(2) + 4c = 2*(2+2c) + 4c = 4 + 4c + 4c = 4 + 8c
        T(8) = 2*T(4) + 8c = 2*(4+8c) + 8c = 8 + 24c
        T(16) = 2*T(8) + 16c = 2*(8+24c) + 16c = 16 + 64c
        
        Pattern: T(n) = n + n*log_2(n)*c

* We'll see other techniques

Solving Recurrence Relations with Recursion Trees
-------------------------------------------------

* It sometimes helps to draw a tree that shows what's happening with the
  recursion.
* We show the size of the problem at each level.
* We can sum across each level, and then sum those sums to get an
  overall estimate of the running time.
* Example stolen from CLRS: T(n) = 3T(n/4) + Theta(n^2)

Solving Recurrence Relations with the Substitution Method
---------------------------------------------------------

* Basically, this is proof by induction.
* We'll assume that the recurrence relation holds for values smaller than *n* 
  and then prove it for *n*.
* Unfortunately, it turns out that there are a lot of subtleties with
  this technique

Solving Recurrence Relations with the Master Theorem
----------------------------------------------------

* The master theorem works for recurrences of the form
  _T(n) = aT(n/b)+f(n)_.
* The computation depends on the relationship between _f(n)_ and
  how quickly the _n/b_ drops to 0.
* There are three rules
    1. If _f(n)_ is in _O(n^(log_b(a)-e))_ for some e > 0, then
    _T(n)_ is in _Theta(n^(log_b(a)))_
    2. If _f(n)_ is in Theta(n^log_b(a)), then
    _T(n)_ is in _Theta(n^(log_b(a)*log n))_
    3. If _f(n) is in Omega(n^(log_b(a)+e))_ for some e > 0, and
    _af(n/b) <= cf(n)_ for some _c_ < 1 and large enough _n_, 
    then _T(n)_ is in _Theta(f(n))_
* There's a simpler version (which I'm taking from Weiss).  This is
  for recurrences fo the form _T(n) = aT(n/b) + O(n^k)_
* There are once again three rules
    1. If a > b^k, then T(n) is in O(n^(log_b(a)))
    2. If a = b^k, then T(n) is in O(n^klog_2(n))
    3. If a < b^k, then T(n) is in O(n^k)
* We'll try some examples.
* _T(n)_ = _9T(n/3) + n_.
* _T(n)_ = _T(2n/3) + 1_.
