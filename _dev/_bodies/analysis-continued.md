Asymptotic analysis, reviewed
-----------------------------

* What have you learned about asymptotic analysis?
* What does it mean for a function to be in O(n), theta(N), omega(N)?
* How does the formality relate to algorithm analysis?

Additional properties of Big-Oh
-------------------------------

* Prove that if f(n) is in O(g(n)) and g(n) is in O(h(n)) then
  f(n) is in O(h(n)).
* What other properties do you expect to be useful?

Careful loop analysis
---------------------

* At times, we want to know an exact value for the number of steps
  executed, rather than a bound.
* And upper bounds can be far too estimated.
* To help us think about these things, it's helpful to do a few
  analyses in depth.
* You have some on your homework.
* We'll work on one together in class.  2-4 from Skiena.

<pre>
function conundrum(n)
  r := 0
  for i := 1 to n do
    for j := i + 1 to n do
      for k := i + j − 1 to n do 
        r := r + 1
  return(r)
</pre>

* Quick and dirty upper bound.  Count the maximum number of repetitions
  of each loop and multiply.
* Accurate assessment: Fun with summations.
