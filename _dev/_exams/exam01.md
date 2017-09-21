---
title: Exam 1
link: true
assigned: 2017-09-20
prologue-due: 2017-09-22
due: 2017-09-27
due-time: 5:00 pm
current: true
---
# {{ page.title }}

*Warning!  This exam is not quite in release form.  It may change until
10:00 p.m. on the day it was assigned.*

**Assigned:** {{ page.assigned | date: '%A, %-d %B %Y' }}

**Prologue Due:** {{ page.prologue-due | date: '%A, %-d %B %Y' }} by {{ page.due-time }}

**Exam Due:** {{ page.due | date: '%A, %-d %B %Y'  }} by {{ page.due-time }}

**Epilogue Due:** {{ page.due | date: '%A, %-d %B %Y' }} by 10:30 p.m.

## Preliminaries

### Exam format

This is a take-home examination. You may use any time or times you deem
appropriate to complete the exam, provided you return it to me by the
due date.

There are five problems on this examination. You must do your best
to answer all of them.  The problems are not necessarily of equal
difficulty. Problems may include subproblems. If you complete five
problems correctly or mostly correctly, you will earn an A.  If you
complete four problems correctly or mostly correctly, you will earn a B.
If you complete three problems correctly or mostly correctly, you will
earn a C.  If you complete two problems correctly or mostly correctly,
you will earn a D.  If you complete fewer than two problems correctly
or mostly correctly, you will earn an F.  If you do not attempt the
examination, you will earn a 0.  Partially correct solutions may or may
not earn you a partial grade, depending on the discretion of the grader.

I rarely give makeup problems because my experience in past semesters
is that students spend a lot of effort on such problems but do not
significantly improve their grade.

*Please read the entire examination before you begin.*

I expect that someone who has mastered the material and works at a
moderate rate should have little trouble completing the exam in a
reasonable amount of time. In particular, this exam is likely to take
you about ten hours, depending on how well you've learned the topics
and how fast you work.

### Blind grading

In the interest of fairness, I prefer to do blind grading on my
examinations.  Assign yourself a random number by typing `(random
1000000)` in Scheme.  You should write your random number on every page
of the exam.  You should do your best to avoid including any information
that would personally identify you within the exam.

### Academic honesty

This examination is open book, open notes, open mind, open computer,
and open Web. However, it is closed person. That means you should
not talk to other people about the exam. Other than as restricted by
that limitation, you should feel free to use all reasonable resources
available to you.

As always, you are expected to turn in your own work. If you find ideas
in a book or on the Web, be sure to cite them appropriately. If you use
code that you wrote for a previous lab or homework, cite that lab or
homework and the other members of your group. If you use code that you
found on the course Web site, be sure to cite that code. You need not
cite the code provided in the body of the examination.

Although you may use the Web for this exam, you may not post your
answers to this examination on the Web.  (You certainly should not post
them to GitHub unless you create a private repository for your exam.)
And, in case it's not clear, you may not ask others (in person,
via email, via IM, via IRC, by posting a "please help"
message on StackOverflow or elsewhere, or in any other way) to put
answers on the Web.

Because different students may be taking the exam at different times,
you are not permitted to discuss the exam with anyone until after I have
returned it. If you must say something about the exam, you are allowed
to say "This is among the hardest exams I have ever taken. If
you don't start it early, you will have no chance of finishing the
exam." You may also summarize these policies. You may not tell
other students which problems you've finished. You may not tell other
students how long you've spent on the exam.

You must include both of the following statements on the cover sheet
of the examination.

> I have neither received nor given inappropriate assistance on this
examination.

> I am not aware of any other students who have given or received
inappropriate assistance on this examination.

Please sign and date each statement. Note that the statements must be
true; if you are unable to sign either statement, please talk to me
at your earliest convenience. You need not reveal the particulars of
the dishonesty, simply that it happened. Note also that inappropriate
assistance is assistance from (or to) anyone other than one of the
two instructors of CSC 301 for this semester.

### Presenting your work

You will only present your exam to me in physical form.

You must write all of your answers using the computer, print them out,
number the pages; and put your assigned number on the top of every page.
You must turn in a separate cover sheet on which you hand write, sign,
and date each of the academic honesty statements (provided you are able
to do so).  If you fail to number the printed pages, you may suffer
a penalty.  If you fail to turn in a legible version of the exam,
you are also likely to suffer some sort of penalty.

*Partial credit.*  I may give partial credit for partially correct
answers. I am best able to give such partial credit if you include a
clear set of work that shows how you derived your answer. You ensure the
best possible grade for yourself by clearly indicating what part of your
answer is work and what part is your final answer.

### Getting help

Do not use Piazza to post your questions.  Send your questions directly
to your instructor via email.

We may not be available at the time you take the exam. If you feel that
a question is badly worded or impossible to answer, note the issue you
have observed and attempt to reword the question in such a way that it
is answerable.  You should also feel free to send me electronic mail at
any time of day.

I will also reserve time at the start of each class next week to discuss
any general questions you have on the exam.

## Prologue

The prologue for this examination will be via email, which you should
send to your instructor.  Your message should be titled
**CSC 301 2017F: Exam 1 Prologue (*your name*)**.

1. *For each problem, please include a short note about something that
will help you solve the problem.* Mostly, we want to see some evidence
that you've thought about the problem.  You might note some similar
procedures you've written or problems you've solved in the past (e.g.,
in this course or another course).  You might note an approach you expect
to use.  You might sketch an algorithm.  You might pose a question to
yourself. (We won't necessarily read this in a timely fashion, so if you
have questions for your instructor, you should ask by email or in person.)

If, when looking at a problem, you think you already know the answer,
you can feel free to write something short like "solved" or "trivial".

2. *Which of those problems do you expect to be the most difficult
for you to solve?  Why?*

3. Conclude by answering the question *What is an approach that you expect
will help you be successful on this exam?* For example, you might suggest
that you will work thirty minutes on the exam each day, or work on the
exam at 7pm each day, when your brain is most able to process information.

## Epilogue

The epilogue for this examination will also be via email, which you
should send to your instructor.  The message should be titled
**CSC 301 2017F: Exam 1 Epilogue (*your name*)**.  Include answers
to the following questions.

*What was the most difficult part of the exam?*

*What made that part difficult?*

*What are two things you can do to be more successful on the next exam?*

## Problems

### Problem 1: Searching for substrings

We have two strings, s and t, where |t| <= |s|.  (The bars
represent "length of".)  Suppose we want to find the starting index of
t within s, assuming that t is a substring of s.  If t
does not appear in s, we will return -1.

```
for i = 0 to s.length - t.length
  if s.substring(i, i+t.length) == t
    return i
  end if
end for
return -1
```

However, string comparison requires us to look at every character in each
string.  That means that this algorithm is O(|s|*|t|).

Skiena suggests that there is an O(|s|+|t|) approach using the
clever hash function.  Implement that approach.

### Problem 2: Revisiting recurrence relations

The master theorem is helpful because it gives us clear bounds on our
recursive functions.  But what if we care as much about the exact
behavior as the asymptotic behavior.  That is, we want to know the
constant multipliers and the lower-order terms.  Not "f(n) is in
O(n^2)", but rather "f(n) = a*n^2 + b*n + c".

Closely approximate each of the following functions.  If you find it
useful, you may assume that *n* is a power of 2 (or 4).  In each case,
you should assume that f(0) = 1 and f(1) = 1.  The recurrences are just
for n>1.

a. f(n) = f(n-1) + c

b. f(n) = 2*f(n/2) + bn

c. f(n) = 2*f(n/2) + bn + c

d. f(n) = 4*f(n/2) + bn

e. f(n) = 2*f(n/4) + bn

f. f(n) = f(n/2) + d*n^2  bn + c

Please explain how you found each result.  (And no, "I looked on Wolfram
Alpha" is not an explanation.)

### Problem 3: Being obstinate about Big-O

We make a wide variety of assumptions about Big-O, such as our ability
to ignore constant multipliers or lower-order terms.  As you saw in a
recent assignment, it is possible to prove that these assumptions are
safe.  Here are a few others.

Prove the following properties of Big-O.  You may assume that all of
the functions produce only positive real numbers.

a. We can ignore lower-order terms.

* if h(n) is in O(g(n) + f(n))
* and f(n) is in O(g(n))
* then h(n) is in O(g(n))

b. We can ignore constant multipliers.

* if f(n) is in O(c*g(n))
* then f(n) is in O(g(n))

c. When two functions have the same bound, their sum also has that bound.

* if f(n) is in O(g(n))
* and h(n) is in O(g(n))
* then (f(n) + h(n)) is in O(g(n))

c. The bound of the sum of two functions is the bound of the two functions.

* if (f(n) + h(n)) is in O(g(n))
* then f(n) is in O(g(n))
* and h(n) is in O(g(n))

### Problem 4: Some sums (or is that sum somes?)

a. What is the result of the following program in terms of `a` and
`b`?  Provide an informal proof or explanation of your answer.

```
result = 0
for (i = a; i <= b; i++)
  result += i
return result
```

b. What is the result of the following program in terms of `k`?
Provide a short inductive proof of your answer.

```
result = 0
for (i = 0; i <= k; i++)
  result += 1/(2^i)
return result
```

c. What is the result of the following program in terms of `n`?
Provide an informal explanation of your answer.

```
result = 0
for (i = 0; i <= n; i++)
  for (j = i; j <= n; j++)
    for (k = j; k <= n; k++)
      result += 1
return result
```

### Problem 5: Removing elements from binary search trees

The following is a relatively complete implementation of binary search 
trees in Scheme/Racket.  However, it lacks a `remove` procedure.  Write
that procedure.

The cost of `remove` should be no worse than the height of the tree.

Since `add` makes no attempt to keep the tree balanced, you do not need
to make your `remove` procedure keep the tree balanced.  

Although there are a variety of unit tests for the extant procedures,
you need not add unit tests for `remove`.  

When submitting your answer to this problem, you need only submit your
code for remove.  (If you also want to submit your unit tests, that's
fine.  But please don't give all of this code back to us.)

```
#lang racket
;;; File:
;;;   bst.rkt
;;; Authors:
;;;   Samuel A. Rebelsky
;;;   Anya Vostinar
;;;   The student sometimes known as 000000
;;; Contents:
;;;   A simple implementation of bsts

(require rackunit)

(provide bst-new)
(provide bst-add)
(provide bst-elements)
(provide bst-find)
(provide bst-remove)
(provide bst-size)
(provide bst-update)

; +-------+----------------------------------------------------------
; | Notes |
; +-------+

; * We represent the nodes of the bst as four-element lists.  Element
;   0 is the key.  Element 1 is the value.  Element 2 is the left subtree.
;   Element 3 is the right subtree.

; * We represent the empty bst as the empty list.

; * We are limiting keys to strings.  Values may be any value other
;   than #f

; +---------------+--------------------------------------------------
; | Local Helpers |
; +---------------+

(define node-key car)
(define node-val cadr)
(define node-left caddr)
(define node-right cadddr)
(define bst-empty? null?)
(define node
  (lambda (key val left right)
    (list key val left right)))
(define empty-bst null)

; +--------------+---------------------------------------------------
; | Constructors |
; +--------------+

;;; Procedure:
;;;   bst-new
;;; Parameters:
;;;   [none]
;;; Purpose:
;;;   Create a new BST
;;; Produces:
;;;   bst, an empty bst
(define bst-new
  (lambda ()
    empty-bst))

; +-----------+------------------------------------------------------
; | Accessors |
; +-----------+

;;; Procedure:
;;;   bst-find
;;; Parameters:
;;;   bst, a binary search tree
;;;   key, a string
;;; Purpose:
;;;   Find the value associated with key in the tree.
;;; Produces:
;;;   val-or-#f, a value
;;; Problems:
;;;   If the key is not in the bst, returns #f
(define bst-find
  (lambda (bst key)
    (cond
      [(bst-empty? bst)
       #f]
      [(string=? key (node-key bst))
       (node-val bst)]
      [(string<? key (node-key bst))
       (bst-find (node-left bst) key)]
      [else
       (bst-find (node-right bst) key)])))

;;; Procedure:
;;;   bst-elements
;;; Parameters:
;;;   bst, a binary search tree
;;; Purpose:
;;;   Produces a list of the key/value pairs in the tree
;;; Produces:
;;;   pairs, a list of lists (in order)
(define bst-elements
  (lambda (bst)
    (if (bst-empty? bst)
        null
        (append (bst-elements (node-left bst))
                (list (list (node-key bst) (node-val bst)))
                (bst-elements (node-right bst))))))

;;; Procedure:
;;;   bst-size
;;; Parameters:
;;;   bst, a binary search tree
;;; Purpose:
;;;   Compute how many elements are in the tree.
;;; Produces:
;;;   size, an integer
(define bst-size
  (lambda (bst)
    (if (bst-empty? bst)
        0
        (+ 1
           (bst-size (node-left bst))
           (bst-size (node-right bst))))))

; +----------+-------------------------------------------------------
; | Mutators |
; +----------+

;;; Procedure:
;;;   bst-add
;;; Parameters:
;;;   bst, a binary search tree
;;;   key, a string
;;;   value, a value
;;; Purpose:
;;;   Adds a key/value pair to the bst
;;; Produces:
;;;   new-bst, a binary search tree
;;; Preconditions:
;;;   [No additional]
;;; Postconditions:
;;;   * If key is already in the bst, new-bst is false.
;;;   * Otherwise, (bst-find new-bst key) => value
;;;   * In either case, bst is not modified
(define bst-add
  (lambda (bst key value)
    (cond
      [(bst-empty? bst)
       (node key value empty-bst empty-bst)]
      [(string=? key (node-key bst))
       #f]
      [(string<? key (node-key bst))
       (let ([new-left (bst-add (node-left bst) key value)])
         (and new-left
              (node (node-key bst)
                    (node-val bst)
                    new-left
                    (node-right bst))))]
      [else
       (let ([new-right (bst-add (node-right bst) key value)])
         (and new-right
              (node (node-key bst)
                    (node-val bst)
                    (node-left bst)
                    new-right)))])))

;;; Procedure:
;;;   bst-remove
;;; Parameters:
;;;   bst, a binary search tree
;;;   key, a string
;;; Purpose:
;;;   Remove the entry with key key from bst
;;; Produces:
;;;   new-bst, a binary search tree
;;; Preconditions:
;;;   [No additional]
;;; Postconditions:
;;;   * (bst-find new-bst key) = #f
;;;   * (assoc key (bst-elements bst)) = #f
;;;   * For all other strings, k, (bst-find new-bst k) = (bst-find bst k)
(define bst-remove
  (lambda (bst)
    bst)) ; STUB

;;; Procedure:
;;;   bst-update
;;; Parameters:
;;;   bst, a binary search tree
;;;   key, a string
;;;   value, a value
;;; Purpose:
;;;   Updates a key/value pair to the bst
;;; Produces:
;;;   new-bst, a binary search tree
;;; Preconditions:
;;;   [No additional]
;;; Postconditions:
;;;   * If key is not already in the bst, new-bst is false.
;;;   * Otherwise, (bst-find new-bst key) => value
;;;   * In either case, bst is not modified
(define bst-update
  (lambda (bst key value)
    (cond
      [(bst-empty? bst)
       #f]
      [(string=? key (node-key bst))
       (node key value (node-left bst) (node-right bst))]
      [(string<? key (node-key bst))
       (let ([new-left (bst-update (node-left bst) key value)])
         (and new-left
              (node (node-key bst)
                    (node-val bst)
                    new-left
                    (node-right bst))))]
      [else
       (let ([new-right (bst-update (node-right bst) key value)])
         (and new-right
              (node (node-key bst)
                    (node-val bst)
                    (node-left bst)
                    new-right)))])))

; +-------+----------------------------------------------------------
; | Tests |
; +-------+

; Empty bst
(define bst0 (bst-new))
(check-= (bst-size bst0) 0 0)

; Singleton bst
(define bst1 (bst-add bst0 "m" "middle"))
(check-= (bst-size bst1) 1 0)
(check-equal? (bst-find bst1 "m") "middle")
(check-false (bst-find bst0 "m") "adding element does not affect original")
(check-false (bst-find bst1 "a"))
(check-false (bst-find bst1 "z"))

; A different singleton bst
(define bst1a (bst-add bst0 "m" "max"))
(check-= (bst-size bst1) 1 0)
(check-equal? (bst-find bst1 "m") "middle")
(check-equal? (bst-find bst1a "m") "max")

; Second element at the right
(define bst2 (bst-add bst1 "z" "zebra"))
(check-equal? (bst-elements bst2) '(("m" "middle") ("z" "zebra")))
(check-false (bst-add bst2 "m" "m"))
(check-false (bst-add bst2 "z" "z"))

; Third element at the left
(define bst3 (bst-add bst2 "d" "dingo"))
(check-equal? (bst-elements bst3) '(("d" "dingo") ("m" "middle") ("z" "zebra")))

; Right then left
(define bst4 (bst-add bst3 "p" "penguin"))
(check-equal? (bst-elements bst4)
              '(("d" "dingo") ("m" "middle") ("p" "penguin") ("z" "zebra")))

; Building a bigger tree
(define elements ; A list of (value key) elements.
  '(("m" "mango")
    ("q" "quince")
    ("a" "avocado")
    ("a" "apple")
    ("b" "banana")
    ("r" "raisin")
    ("t" "turnip")
    ("o" "orange")
    ("n" "nectarine")
    ("p" "plum")
    ("c" "cherry")
    ("s" "strawberry")))
(define mutable
  (vector (bst-new)))
(for-each (lambda (pair)
            (vector-set! mutable 0
                         (bst-add (vector-ref mutable 0)
                                  (cadr pair) (car pair))))
          elements)
(check-equal? (bst-elements (vector-ref mutable 0))
              (sort (map (lambda (entry) (list (cadr entry) (car entry)))
                         elements)
                    (lambda (v1 v2)
                      (string<=? (car v1) (car v2))))
              "All of the elements are there in the right order.")

; I should be able to find all of the keys
(for-each (lambda (pair)
            (check-equal? (bst-find (vector-ref mutable 0)
                                    (cadr pair))
                          (car pair)
                          (string-append "Looking for " (cadr pair))))
          elements)

; I should not be able to add any of the keys
(for-each (lambda (pair)
            (check-false (bst-add (vector-ref mutable 0)
                                  (cadr pair) (cadr pair))))
          elements)

; Update all of the pairs (check update)
(define updated (vector (vector-ref mutable 0)))
(for-each (lambda (pair)
            (vector-set! updated 0
                         (bst-update (vector-ref updated 0)
                                     (cadr pair) (cadr pair))))
          elements)

; The elements should be the same.
(check-equal? (bst-elements (vector-ref updated 0))
              (sort (map (lambda (entry) (list (cadr entry) (cadr entry)))
                         elements)
                    (lambda (v1 v2)
                      (string<=? (car v1) (car v2))))
              "All of the elements are there in the right order.")

; I should be able to find all of the keys
(for-each (lambda (pair)
            (check-equal? (bst-find (vector-ref updated 0)
                                    (cadr pair))
                          (cadr pair)
                          (string-append "Looking for " (cadr pair))))
          elements)
```

## Questions and answers

We will post answers to questions of general interest here while the exam is in
progress. Please check here before emailing questions!

