---
title: Exam 2
link: true
assigned: 2017-11-08
due: 2017-11-15
due-time: 5:00pm
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

I may not be available at the time you take the exam. If you feel that
a question is badly worded or impossible to answer, note the issue you
have observed and attempt to reword the question in such a way that it
is answerable.  You should also feel free to send me electronic mail at
any time of day.

I will also reserve time at the start of each class next week to discuss
any general questions you have on the exam.

## Prologue

The prologue for this examination will be via email, which you should
send to your instructor.  Your message should be titled
**CSC 301 2017F: Exam 2 Prologue (*your name*)**.

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
**CSC 301 2017F: Exam 2 Epilogue (*your name*)**.  Include answers
to the following questions.

*What was the most difficult part of the exam?*

*What made that part difficult?*

*What are two things you can do to be more successful on the next exam?*

## Problems

### Problem 1: Balanced trees

a. Draw the red-black tree that results from inserting the following
sequence of values into the empty tree: aardvark, baboon, chinchilla,
dingo, emu, fox, gibbon, hippo, iguana, jackalope, and koala.  (You
may find it useful to show the intermediate steps.)

b. Draw the two-three tree that results from inserting the same
sequence of values into the empty tree.

c. Draw the red-black tree that results from removing gibbon from
the tree you created in step a.

d. Draw the two-three three that results from removing gibbon from the
tree you created in step b.

### Problem 2: Trying tries

In class, we built a trie to help us count the number of words in a
collection that started with a particular prefix.  But what if we
want to identify not the number of words that start with a
given prefix, but rather the actual words that start with the given
prefix.  We can imagine three basic commands for such a system: we
can add a new string (`save`), we can get a list of strings that start
with a prefix (`find`), and we can remove a string (`drop`).

```
save sam
save samuel
save sample
save samples
find sam
sam
sample
samples
samuel
save samantha
save samwise
save sampling
find samp
sample
sampling
drop sam
drop sample
find sam
samantha
samples
sampling
samuel
samwise
```

As you might expect, tries continue to provide an excellent mechanism
for solving this problem.

Write a C program, `predict`, that reads and responds to a sequence
of commands of the form above.

* When you encounter a `save` command, you should store the associated
  string in the trie.
* When you encounter a `find` command, you should print out the strings
  that start with a given prefix in alphabetical order.  If one string
  is a prefix of another, you should print out the prefix first
  as in the `sam`, `sample`, `samples` example.
* When you encounter a `drop` command, you should remove the string
  from the trie (or mark it as removed).

You may assume that no string is more than 31 characters.  You may
assume that the strings contain only lowercase letters.

### Problem 3: Randomly selecting courses

Professor P and his advisee are working on preregistration.  While
they've agreed on the first three courses, they are debating what
the student should take for the fourth course.  It could be an
humanities course or it could be be a social science course.  They've
made a list of possible courses.  They decide to repeatedly apply
the following process for narrowing down the list of courses.

* Randomly pick two courses from the list.
* If the two courses are in the same division, that's a sign that
  that division dominates too much.  Get rid of both courses.  But
  to make sure that we still have a reasonable selection, add a
  new humanities course to the list.  (You can assume that there
  are arbitrarily many new humanities courses to add.)
* If the two courses are in different divisions, keep the social
  science and drop the humanities course.  (Dropping the humanities
  course in this case conceptually offsets the addition of the
  humanities course in the prior case.)

I didn't say that it was a sensible approach.  Just that it was an
approach.  Still, my advisees may be familiar with it.

a. Prove that the process terminates with only one course.

b. Write a loop invariant that provides useful information about the
state of the system.

c. Using that invariant, determine the division of the final course
based on the number of initial courses in each division.

### Problem 4: Extending a minimum spanning tree

Suppose we are given a graph G(V,E) *and* a minimum spanning tree G(V,E')
of that graph.  Give an O(n) algorithm to find the minimum spanning tree
of the graph G(V,E+{<u,v,w>}), where <u,v,w> represents an undirected
edge between u and v of weight w.

That is, write an efficient algorithm that rebuilds a minimum spanning
tree when an edge is added to a graph for which you've already built the
MST.

## Questions and answers

We will post answers to questions of general interest here while the exam is in
progress. Please check here before emailing questions!

