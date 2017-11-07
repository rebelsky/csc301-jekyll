---
title: Front Door
---
# {{ site.title }}

**Warning!  The class site is currently under development.  Expect things
to change significantly.**

  <dl class="dl-horizontal">
    <dt>Instructor</dt>
    <dd>
      <a href="{{ site.data.info.instructor_homepage }}">{{ site.data.info.instructor }}</a>
    </dd>
  
    <dt>Meeting Times</dt>
    <dd>{{ site.data.info.meeting_times }}</dd>
  
    <dt>Office Hours</dt>
    <dd>{{ site.data.info.office_hours }}</dd>
    <dd>I also tend to follow an open door policy: Feel free to
      stop by when my door is open to to make an appointment for
      another time.</dd>

    <dt>Class Mentors</dt>
    <dd>
      <ul class="list-unstyled">
        {% for mentor in site.data.info.mentors %}
          <li>{{ mentor }}</li>
        {% endfor %}
      </ul>
    </dd>
  </dl>

## About this course

Welcome to the Fall 2015 section of Grinnell College's *CSC 301 -
Algorithm Analysis*.  CSC 301 is the department's advanced course
in algorithms and serves as a successor to CSC 207, Algorithms and
Object-Oriented Design.  In this course, we will work to develop your
skills in the design, implementation, analysis, and verification of
algorithms, abstract data types, and data structures.  

Along the way, we will consider a variety of classic algorithms, ADTs,
and data structures - the "literature" of CS, as it were.  Why do we
read the literature?  Because knowing how problems have been solved in
the past helps us solve future problems.  A not-so-recent article on 
mathematics suggests the value of knowing the literature.

> Yet, as they told me, the proof [of the Green-Tao Theorem] depended
on the insights of many other mathematicians. In the game of devil's
chess [mathematics], players have no real hope if they haven't studied
the winning games of the masters. A proof establishes facts that can
be used in subsequent proofs, but it also offers a set of moves and
strategies that forced the devil to submit — a devious way to pin
one of his pieces or shut down a counterattack, or an endgame move that
sacrifices a bishop to gain a winning position. Just as a chess player
might examine variations of the Ruy Lopez and King's Indian Defense,
a mathematician might study particularly clever applications of the
Chinese remainder theorem or the sieve of Eratosthenes. The wise player
has a vast repertoire to draw on, and the crafty player intuits the move
that suits the moment.

> Cook, Gareth (2015).  The Singular Mind of Terry Tao.  *The New
York Times Magazine*.  26 July 2015.  Available online at <http://www.nytimes.com/2015/07/26/magazine/the-singular-mind-of-terry-tao.html>.

This course will certainly expand your "repertoire to draw on".
