Course Goals
------------

* Build skills in designing
    * Algorithms
    * Abstract Data Types - Generalizations that we give to 
      organizations of data - What you can do with the data, not
      how you do it.  (Interface)
    * Data Structures (Class)
* Review "the literature"
    * Often with an active-learning approach
* More formally!  Proof.
    * Correctness.
    * Running time
    * Minimum possible running time for a solution
* New techniques for designing algorithms
    * Randomness
    * Approximation (maybe)

Course Format
-------------

* Some lecture
* Lots of small-group/large-group problem solving
* I would prefer that you *not* read the textbooks in advance of our
  discussion of a topic. You learn the techniques better by trying to
  apply them than by just reading them. You learn key algorithms and
  data structures better if you've had to design them.

Approaching Algorithms
----------------------

*You are now experienced computer science students.  When some gives
you a problem that admits algorithms solution, what do you do?*

* Here's one approach
    * Try some examples by hand
    * Attempt to generalize your solution
    * Try the generalized solution on other problems
    * Write some unit tests
    * Turn the generalized solution into code
    * Analyze the algorithm
    * Try to improve
* Here's another approach
    * Find a related problem and related solution
    * Adapt the solution
    * Try the adapted solution on other problems
    * Write some unit tests
    * Turn the generalized solution into code
    * Analyze the algorithm
    * Try to improve
* We are going to add a few important steps
    * Try to break the algorithm.  Think carefully about situations
      in which it will fail (or fail to work quickly)
    * Prove the algorithm correct

Problem: Getting From Here to There
-----------------------------------

* Let's pretend that net neturality fails.
* We now have a problem: We need to get information from place to place,
  and we may want the least expensive path, or the quickest, or ...
* We model the problem

Problem: Optimal Soldering Plans
--------------------------------

*Stolen/modified from Skienna*

* We have a bunch of points that we need to have a robot solder
  on a circuit board.
* We want the least wear and tear on the robot.
* How do we determine how to order the points?

Problem: Scheduling Overlapping Tasks
-------------------------------------

*Stolen/modified from Skienna*

* You have a bunch of tasks, each of which has a start time and a length?
* You can only do one task at a time.
* How do you maximize the number of tasks you complete?

Extension

* What if each task also has a value?  How do you maximize the value
  of the tasks you complete?

