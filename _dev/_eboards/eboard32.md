---
title: Eboard 32  Sets and union-find
number: 32
section: eboards
held: 2017-11-13
---
CSC 301.01, Class 32:  Sets and union-find
==========================================

_Overview_

* Preliminaries
    * Notes and news
    * Upcoming work
    * Extra credit
    * Questions
* A set ADT
* Data structure design, revisited
* The union-find structure
* Analyzing union find
* Improving union-find

### News / Etc.

* I expect that most upper-level CS classes will fill this semester.
  You help the department better consider stress points and how to address
  them if you register earlier, rather than later.
* Prof. French noted that Kruskal's algorithm serves as second purpose:
  It allows you to count the number of conntected components in a graph.
* The due date of Exam 2 has been pushed to Friday.

### Upcoming work

* [Exam 2](../exams/exam02) due Friday at 4:00 p.m.
* Read Skiena 6.1-6.4 for Wednesday (or Friday).

### Extra Credit (Academic/Artistic)

* CS Table, Tomorrow
* Convocation Thursday at 11 a.m. in JRC 101.  "Work's Provocative Future: 
  Which Graduates Will Thrive?"

### Extra credit (Peer)

* Pub-Free Quiz: Math/Stats, Wednesday
* Swim meet, Saturday
* Orchestra Saturday at 2pm in Sebring Lewis

### Extra Credit (Misc)

### Other good things

* "The First Time I Walked on the Moon".  Thursday 7:30, Friday 7:30,
  Saturday 2:00, Saturday 7:30, Sunday 2:00.
* Fresh Flutes Thursday
* Voice recitals Friday at 4:15 (Henderson) and 7:00 (Manuel)
* Women's Basketball vs. Emmaus Wed at 5:00 p.m.
* Men's Basketball vs. Emmaus Wed at 7:00 p.m.

### Questions

How do I do part c of problem 3?  (That is, how do I determine the final value based on the initial values, given that things are random?)
  : A good invariant will help.

Should we prove the invarant correct
  : A good argument suffices.

Does pseudocode suffice for the online algorithm?
  : Psuedocode is fine.  But you do need to argue that it's O(n).
  : A description is also fine. But you do need to argue that it's O(n).

For problem 4: Are v and u already in the graph?
  : Maybe.  At least one is.  You may suppose wlog that v is in the graph.
  : "wlog" = "without loss of generality"

Does that mean we need to check if it's already in the graph?
  : It seems so.

Can we use existing algorithms and their running time?  
  : Certainly.

Can we use the Web site that builds red-black trees for you?
  : Yes, if you cite it.
  : But you might want to build them yourself, first.

Do we have to prove that our solution to #4 is correct?
  : No.

Do we have an in-class final?
  : Yes.

I have two in-class finals that day.  Will you find another time?
  : Yes.

When is our final?
  : Wednesday at 9am!

Next Wednesday?
  : No.  Wednesday of finals week.

A set ADT
---------

Suppose we have a program that requires us to deal with sets.

* What goes in the set interface?  (Alternately: What operations do
  you want as you deal with sets?)

* `set.add!(value)` or `set.add(value) => set`
* `set.remove!(value)` or `set.remove(value) => set`
* `set.contains?(value) => boolean`
* `set.union!(set)` or `set.union(set) => set`
* `set.intersect!(set)` or `set.intersect(set) => set`
* `set.subtract!(set)` or `set.subtract(set) => set`
* `set.disjunction!(set)` or `set.disjunction(set) => set`
* `set.filter(proc) => set`
* `set.subsetOf?(set) => boolean`
* `set.reduce(binproc) => val`
* `set.map(proc) => set`
* `set.product(set) => set`
* `set.iterate(proc)` or `set.iterator() => Iterator`.

Data structure design, revisited
--------------------------------

* Sometimes it's better to focus on the particular things you need for
  a particular task, rather than the "kitchen sink" approach.
* We will look at a small set of operations and consider how to implement
  them efficiently.
* `SetOfSets.set-of-one(val)`
* `SetOfSets.union!(set,set)`
* `SetOfSets.find-set(val)`
* Assume that each value can only be in one set.
* Note: We will use `find-set` primarily to determine if two values are in
  the same set.

What strategies might you use?

* "hash tables"
* "trees"

Examples

* Values a, b, c, d, e,f are all in separate sets.
* We union the {a} and {b} sets, giving us {a,b}
* We union the {a,b} and {c} sets, giving us {a,b,c}
* We union the {d} and {e} sets, giving us {d,e}
* We union the {a,b,c} and {d,e} sets, giving us {a,b,c,d,e}
* We union the {a,b,c,d,e} and {f} sets, giving us {a,b,c,d,e,f}

The union-find structure
------------------------

* Represent each set as a directed graph: An upside-down tree.
  Children point to parents.
* The root is the representative element (what we get from find-set)
* How do we keep the tree shallow?
    * When unioning two trees, have the root of the smaller one point 
      to the root of the bigger one.
    * Our height will never be bigger than log(n).  
* So we now have union is O(1) and find is O(logn)
    * union could be O(logn) if we need to find the root
* Keep the size in each tree so that we know which is smaller
* Note: This is *really* helpful for Kruskal's, which repeatedly asks
  if an edge joins two different components

Analyzing union find
--------------------

Improving union-find
--------------------

* Whenver you run find, update the links from every element along the
  way.

Kruskal's counts connected components
-------------------------------------
