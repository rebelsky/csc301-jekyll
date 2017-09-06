---
title: Eboard 06  Asymptotic analysis and recurrence relations
number: 06
section: eboards
held: 2017-09-06
current: true
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
* [Assignment 2](../assignments/assignment02), due 10:30 pm TONIGHT.
    * Papers under my door.
* [Assignment 3](../assignments/assignment03), due 10:30 pm next Wednesday

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

* ???

### Extra Credit (Misc)

* Host a prospective student

### Other good things

* Women's Soccer vs. Central, TODAY at 5:00 p.m., Springer Field
* Les Duke Cross Country Meet, Saturday at 9 a.m., Country Club
* Women's Tennis vs. Beloit and Lake Forest, Saturday at 9 am Fieldhouse
* Men's Soccer vs. North Central College, Saturday at 1:00 p.m., Springer Field
* Women's Soccer vs. University of Wisconsin-Oshkosh, Sunday at 1:00 p.m., Springer Field

### Questions

The median algorithm, revised
-----------------------------

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

Let's run the algorithm.

Two generic divide-and-conquer algorithms
-----------------------------------------

Modeling the running time of the generic algorithms
---------------------------------------------------

Estimating the running time
---------------------------

Looking ahead: The master theorem
---------------------------------

