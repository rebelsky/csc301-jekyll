---
title: Preliminaries for class 4
section: prelim 
link: true
---
### News / Etc.

* The Web site is still under development.  Expect some significant
  changes to the topics, but not to the timing of homework assignments
  and examinations.
* Check in: Daily note-taking responsibilities.
* I know that many other computer scientists, including textbook authors, 
  write things like "f(n) = O(g(n))".  I expect you to be more careful.
  if O(g(n)) is a set of functions and f(n) is a function, we know that
  they can't be equal.  Use the "element-of" operation, which I may
  denote in text as "in".

### Upcoming work

* Read CLRS 3 for Monday.
* [Assignment 2](../assignments/assignment02), due 10:30 pm next Wednesday.

### Some preliminary notes on HW1

1. Good practice is to include instructions for running your code
(typically, in a README file), a log of your code running, or both.

2. When you submit code, I really do want you to send me tarballs of
directories named with your userid or userids.  That way, I don't end
up with twenty-four directories named things like "Assignment 1".

3. I did expect you to document what your own heuristic was.  

4. I did expect you to think a bit about what the results said and how
you presented them.  Consider, for example, the following excerpt from
the output of one of your programs.

   ```
   Round= 7
   Random distance=345.81228057523197
   diagonal distance=332.1423102983489
   custom distance=332.1423102983489
   closest distance=33.24154027718932
   ```

That's strange, isn't it?  Are you confident that the output is correct?
Wouldn't you like to know what the points are?

5. We should talk a bit about the time required for this assignment
and the difficulty of the assignment.  Some of you said that this was
a hard assignment.  I had intended to be a simple assignment.

   Here's my thinking:
   
   > Nothing in it is conceptually complex or novel.  In part 1, you are
   re-implementing a data structure you should know in a language you
   should know.  In part 2, you were writing procedures to reorder a list
   or vector of values.  You should have done that dozens of times by now.

   > The hard element of part 1 was likely refreshing your Scheme knowledge.
   The hard element of part 2 was likely picking the right language.  If
   you did not pick an easy-to-use language, I expect that the problem
   was harder.

   A colleague suggests that I didn't consider carefully enough how the 
   different components of each would increase the complexity.

6. Quick: How many calls to `list-index` are there in the following
code if the element we are searching for is the tenth element of the
list?

```
; Code taken from https://stackoverflow.com/questions/13562200/find-the-index-of-element-in-list
(define list-index
  (lambda (e lst)
    (if (null? lst)
        -1
        (if (eq? (car lst) e)
            0
            (if (= (list-index e (cdr lst)) -1) 
                -1
                (+ 1 (list-index e (cdr lst))))))))
```

### Extra credit (Academic)

* _The Big Sick_, Tonight, Harris.
* Rosenfield symposium, next week.  (Lots of different events)

### Extra credit (Peer)

* *Try out for Ritalin Test Squad!*  RTS is having a joint audition with
  IC this weekend from 12-3 in The Wall (Bucksbaum 154). People can email
  [improv] or [lfimprov] for more information or if they want to get emails
  about our shows, open practices, and events.

### Extra Credit (Misc)

* Community Hour (Dialogues Across Difference), Tuesday at 11 a.m. in JRC 209.
* CLS Kick-Off Event, Tuesday at 11 a.m. in "North Campus Grove".

