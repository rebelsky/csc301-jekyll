---
title: Eboard 06  Asymptotic analysis and recurrence relations
number: 06
section: eboards
held: 2017-09-06
---
CSC 301.01, Class 06:  Asymptotic analysis and recurrence relations
===================================================================

_Overview_

* Preliminaries
    * Notes and news
    * Upcoming work
    * Extra credit
    * Questions
* The median algorithm, revised
* Two generic divide-and-conquer algorithms
* Modeling the running time of the generic algorithms
* Estimating the running time
* Looking ahead: The master theorem

### News / Etc.

* I may take attendance.

### Upcoming work

* Reading for Friday: CLRS 4.
    * Some of it won't make sense.  That's okay.
* [Assignment 2](../assignments/assignment02), due 10:30 pm TONIGHT.
    * Papers under my door.
* [Assignment 3](../assignments/assignment03), due 10:30 pm next Wednesday
    * Does not have to be in LaTeX
    * Goal of getting some insight into the running time of recursive
      procedures.

### Extra credit (Academic)

* Convocation, Thurday at 11:00 a.m. in JRC 101: The Des Moines
  Agricultural Corridor.
    * Why you should attend *every* convocation.
* Rosenfield symposium, this week.  (Lots of different events)
    * Jason Reblando, photographer and author, describing "New Deal Utopias," at 4 p.m. TODAY in JRC 101.
    * Alan Durning of Sightline Institute, stressing “The Power of Small: How Building Small Means Living Large,” 7:30 p.m. TODAY in JRC 101
    * Shu-Yang Lin, re:architect at Public Digital Innovation Space, presenting “Democracy from the Future: Taiwan” at 4 p.m. Thursday, Sept. 7 in JRC 101.
    * Tom Vilsack, former Iowa Governer, "Food as a Political Movement that
      Unites but Does Not Divide" at 7:30 p.m. Thursday, Sept. 7 in JRC 101.

### Extra credit (Peer)

* A week from Friday is the CS picnic.  Sign up when you get the email.

### Extra Credit (Misc)

* Host a prospective student email [ohc] (overnight host coordinator)

### Other good things

* Women's Soccer vs. Central, TODAY at 5:00 p.m., Springer Field
* Les Duke Cross Country Meet, Saturday at 9 a.m., Country Club
* Women's Tennis vs. Beloit and Lake Forest, Saturday at 9 am Fieldhouse
* Men's Soccer vs. North Central College, Saturday at 1:00 p.m., Springer Field
* Women's Soccer vs. University of Wisconsin-Oshkosh, Sunday at 1:00 p.m., Springer Field

### Questions

For f(n) vs g(n) what do we submit as the explanation?
  : f(n) is most like h(n) except for a constant multiplier.  If I look
    up h(n) and g(n) in the table in the book, I see that ...

What do you want for extra credit?
  : Two paragraphs, reflective, within two days of the event if possible.

The median algorithm, revised
-----------------------------

Idea: We will find the median in an array by trying to move the median
to the middle and then looking in the middle.

Algorithm: Pick a pivot.  Partition.  Ignore clearly impossible stuff.
Recurse.

Note: Partitioning has a goal of getting everything less than the pivot
to the left of the pivot and everything greater than the pivot to the right.

Here's a list of 19 randomly generated integers.

```
> (define random-list
    (lambda (n)
      (if (zero? n)
          null
          (cons (random 100)
                (random-list (- n 1))))))
> (random-list 19)
'(63 70 49 4 55 49 90 97 71 53 93 17 46 34 90 50 95 7 31)
```

To partition: 

* We have a pointer at the left of the sublist and a pointer at the 
  right of the sublist.
* If the thing at the left is less than or equal to the pivot, advance
  the left pointer.
* If the thing at the right is greater than or equal to the pivot, retreat
  the right pointer.
* Swap the left and right, provided they haven't crossed.
* Do it all again.
* At the end, swap the pivot with the rightmost thing in the smaller
  section.

Let's run the algorithm.

```
'(63 70 49 04 55 49 90 97 71 53 93 17 46 34 90 50 95 07 31)
     l                                                  r
swap
'(63 31 49 04 55 49 90 97 71 53 93 17 46 34 90 50 95 07 70)
        l                                            r
advance l
'(63 31 49 04 55 49 90 97 71 53 93 17 46 34 90 50 95 07 70)
                    l                                r
swap
'(63 31 49 04 55 49 07 97 71 53 93 17 46 34 90 50 95 90 70)
                       l                          r   
retreat r
'(63 31 49 04 55 49 07 97 71 53 93 17 46 34 90 50 95 90 70)
                       l                       r      
swap
'(63 31 49 04 55 49 07 50 71 53 93 17 46 34 90 97 95 90 70)
                          l                 r         
retreat r
'(63 31 49 04 55 49 07 50 71 53 93 17 46 34 90 97 95 90 70)
                          l              r   
swap
'(63 31 49 04 55 49 07 50 34 53 93 17 46 71 90 97 95 90 70)
                             l        r      
advance l
'(63 31 49 04 55 49 07 50 34 53 93 17 46 71 90 97 95 90 70)
                                 l    r      
swap
'(63 31 49 04 55 49 07 50 34 53 46 17 93 71 90 97 95 90 70)
                                   lr 
advance l
'(63 31 49 04 55 49 07 50 34 53 46 17 93 71 90 97 95 90 70)
                                   r  l
swap pivot
'(17 31 49 04 55 49 07 50 34 53 46 63 93 71 90 97 95 90 70)
                                   lr
We know that 63 and above can't be the median.  Try again
'(17 31 49 04 55 49 07 50 34 53 46 63 93 71 90 97 95 90 70)
      l                          r
retreat r
'(17 31 49 04 55 49 07 50 34 53 46 63 93 71 90 97 95 90 70)
      l             r
swap
'(17 07 49 04 55 49 31 50 34 53 46 63 93 71 90 97 95 90 70)
        l        r
retreat r
'(17 07 49 04 55 49 31 50 34 53 46 63 93 71 90 97 95 90 70)
        l  r
swap
'(17 07 04 49 55 49 31 50 34 53 46 63 93 71 90 97 95 90 70)
        r  l
swap the pivot
'(04 07 17 49 55 49 31 50 34 53 46 63 93 71 90 97 95 90 70)
We know the median is between l and r, inclusive
'(04 07 17 49 55 49 31 50 34 53 46 63 93 71 90 97 95 90 70)
           l                    r
``` 

```
Two generic divide-and-conquer algorithms
-----------------------------------------

```
def alg input
  if (small? input)
    return base-case-computation input
  else
    (part1,part2) = split input
    soln1 = alg part1
    soln2 = alg part2
    return combine(soln1,soln2)

def alg input
  if (small? input)
    return base-case-computation input
  else
    (part1,part2) = split input
    if (some-test? input)
      return update(alg part1)
    else
      return update(alg part2)
```

Modeling the running time of the generic algorithms
---------------------------------------------------

For the "recurse on both sides algorithm"

Idea: Write a function that represents the running time.  T(n) is the
running time of our algorithm on an input of size n.

```
T_alg(n) =~ T_split(n) + 2*T_alg(n/2) + T_combine(n/2,n/2)
```

Typical form:

```
T(1) = d
T(n) = cn + 2*T(n/2)
```

Estimating the running time
---------------------------

How would you figure out what T(n) is in "closed form"?  (No recursive
component.)

### Option 1: Expand plus intuition

```
T(n) = cn + 2*T(n/2) 
     = cn + 2*(c*n/2 + 2*T(n/4)) ; replace
     = cn + cn + 4*T(n/4) ; simplify
     = 2*cn + 4*T(n/4) ; simpilfy
     = 2*cn + 4*(c*n/4 + 2*T(n/8))
     = 3*cn +  8*T(n/8) ; simplify
     = Pattern!  k*cn + 2^k*T(n/2^k)
When k is log_2(n) ...
```

### Option 2: Upwards

```
T(1) = 1
T(2) = 2c + 2*T(1) = 2c + 2
T(4) = 4c + 2*T(2) = 4c + 2*(2c + 2) = 8c + 4
```

### Option 3: Tree

Pretty clearly Theta(nlogn).

### Option 4: Look it up in a formula.

Looking ahead: The master theorem
---------------------------------

