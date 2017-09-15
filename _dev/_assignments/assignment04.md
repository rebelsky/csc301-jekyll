---
title: Assignment 4
link: true
assigned: 2017-09-13
due: 2017-09-20
due-time: 10:30pm
---
# {{ page.title }}

*Due*: {{ page.due | date: '%A, %-d %B %Y' }} by {{ page.due-time }}

*Summary*:

*Purpose*:

*Collaboration* (code): You may discuss this assignment with anyone you
like, provided you credit such discussion when you submit the assignment.
You will learn more if you do most of the coding on your own, but you
may choose to submit the code for the assignment as a pair or trio.

*Collaboration* (written): You may discuss this assignment with anyone you
like, provided you credit such discussion when you submit the assignment.
You will find that you learn the material better more if you follow 
initial design discussions in a group with individual writing.  Each 
person should write up his, her, zir, or their own work and submit it
individually.

*Submitting* (code): Create a tarball from your code and then mail it
to your course instructor with a subject of **CSC 301 Assignment {{
page.number }} (Your Name)**.  You should, of course, substitute your
name in that subject.

*Submitting* (written): Turn in your work under my office door.  While I
would prefer that you use LaTeX, you may certainly do your work by hand.
Make sure to include your name, course information, and date at the
top of the page.  If you use paper torn from a loose-leaf notebook,
make sure to remove or trim any lose edges.

*Evaluation*: We will primarily evaluate your work on its *correctness*
(e.g., does it compute what it is supposed to; does it meet the
requirements of the assignment); *clarity* (e.g., is it easy to read,
is it well formatted and documented); and *efficiency* (e.g., does it
achieve its goal quickly and with limited resources).  These criteria
will be modified, as appropriate, for written and coding assignments.

*Warning*: So that this assignment is a learning experience for everyone,
we may spend class time publicly critiquing your work.

## Part 1: Hash tables

Implement chained (a.k.a. "bucketed") hash tables in Scheme.
Your keys will be strings.  Your values will be arbitrary Scheme
values.  You should provide `add`, `update`, `find`, and `delete`
procedures.  `add` should report an error to the caller if the key
is already in the table and `update` should report an error to the
caller if the key is not already in the table.

Your table should grow when it is more than 50% full.

Use the Skiena "sum of powers" for the hash function.

Use unit tests to verify that key/value pairs are appropriately added,
updated, and removed.

You need not test your hash function.

Bonus: Parameterize the hash table "constructor" to permit changing some 
or all of these policies (e.g., the percent at which you expand, the
hash function).

## Part 2: Sets of Strings

Sets can be useful for a variety of situations.  Suppose we have decided
to have a "Set of Strings" abstract data type with the following methods.

* `add(set,val)`, which adds a value to a set.
* `contains(set,val)`, which determines if a set contains a value.
* `union(set,set)`, which creates a new set that represents the union
  of two sets.
* `intersect(set,set)`, which creates a new set that represents the
  intersection of two sets.

a. Describe three reasonable implements of this ADT.

b. For each, indicate that asymptotic cost of each method.  In determining
the asymptotic cost of each method, make sure that you consider not only
the size of the set (`n`), but also the length of the string (`m`).

c. Suppose you had to implement a `remove(set,val)` method.  How would
that affect your choice of representation?

