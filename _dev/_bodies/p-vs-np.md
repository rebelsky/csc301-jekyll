Running Times
-------------

* As you've seen, we strive to write algorithms with the "smallest"
  asymptotic lower bounds.
    * History shows that over time, constant multipliers become less
      important than the shape of the curve.
* We classify algorithms by their running time or space usage.
* Most of our algorithms are O(n^3) or less.
* We've seen some exhaustive algorithms that are 
  O(n!) or O(2^n) or equivalent.
* The latter functions grow fast enough that we can't really run them
  on any interesting size input.
* What do we do?

TSP
---

* The Travelling Salesperson Problem is one of the famous problems
  that has an obvious exhaustive solution.
* Given a set of cities and distances between them, find the shortest path
  that visits all of the cities without repeating any city.
    * Alternate formulation: Determine whether there is a path shorter than
      a certain length.
* Exhaustive solution: Generate every path and take the shortest.

Satisfiability
--------------

* The Boolean Satisfiability Problem (SAT) is a fairly straightforward
  problem: Given an expression over n Boolean values, is there a
  set of assignments to those values for which the expesssion holds?

Approaches to Exponential-Time Algorithms
-----------------------------------------

* We should try to develop more efficient algorithms for such problems.
* What do we do if we can't?
* One approach: Accept a "good enough" answer.  
    * I think Skienna gives us a solution to TSP that is no worse than
      two times the shortest path.
* Another approach: Prove that there is no faster solution.
    * We did that with sorting
* But what if you don't want a good-enough answer and can't do the proof?

Complexity Classes
------------------

* Computer scientists sometimes study these kinds of questions by classifying
  problms and seeing what they can say about sets of problems.
* Two famous complexity classes
   * P - The problems that we can solve in O(n^p) for some p.
   * NP - The problems whose solutions we can *verify* in O(n^p) for some p.
* P is clearly a subset of NP.  But is it a proper subset?

NP-Complete Problems
--------------------

* There are a class of problems, called the NP-complete problems, that
  have a special property: If we can solve any of them in polynomial time,
  we can solve every problem in NP in polynomial time.
* How do we achieve that property?
* We show how to transform any instance of any problem in NP into an 
  instance of that problem in polynomial time.
    * Actually, we show that we can transform any instance of one
      NP-complete problem into an instance of that problem.
    * Since the NP-complete problem already has the property we want ...
