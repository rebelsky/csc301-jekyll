---
title: "Assignment 6: Skip lists"
link: true
assigned: 2017-10-04
due: 2017-10-25
due-time: 10:30pm
---
# {{ page.title }}

*Due*: {{ page.due | date: '%A, %-d %B %Y' }} by {{ page.due-time }}

*Summary*: You will implement skip lists, a famous randomized data
structure.

*Purpose*: To give you experience working from "the literature".  To
help you think more about the power of randomization.

*Collaboration* (code): You may discuss this assignment with anyone you
like, provided you credit such discussion when you submit the assignment.
You will learn more if you do most of the coding on your own, but you
may choose to submit the code for the assignment as a pair or trio.

*Submitting* (code): Create a tarball from your code and then mail it
to your course instructor with a subject of **CSC 301 Assignment {{
page.number }} (Your Name)**.  You should, of course, substitute your
name in that subject.

*Evaluation*: We will primarily evaluate your work on its *correctness*
(e.g., does it compute what it is supposed to; does it meet the
requirements of the assignment); *clarity* (e.g., is it easy to read,
is it well formatted and documented); and *efficiency* (e.g., does it
achieve its goal quickly and with limited resources).  These criteria
will be modified, as appropriate, for written and coding assignments.

*Warning*: So that this assignment is a learning experience for everyone,
we may spend class time publicly critiquing your work.

Read the following article.

William Pugh. 1990. Skip lists: a probabilistic alternative
to balanced trees. _Commun. ACM_ 33,
6 (June 1990), 668-676. DOI=10.1145/78973.78977.
<http://doi.acm.org/10.1145/78973.78977>.

Then implement skip lists in either Scheme, C, or Java.  Your implementation
should include a procedure that prints out the current state of the skip
list.  (You may find it easier to print them vertically, rather than
horizontally.)  You should also provide an appropriate test suite.

*Note* Although you can easily find some implementations online, you will
not gain the necessary understanding if you rely on those implementations.
As one of my colleagues says, "There's a benefit to the **** of debugging
a data structure."
