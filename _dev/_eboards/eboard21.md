---
title: Eboard 21  Tries
number: 21
section: eboards
held: 2017-10-11
---
CSC 301.01, Class 21:  Tries
============================

_Overview_

* Preliminaries
    * Notes and news
    * Upcoming work
    * Extra credit
    * Questions
* Introduction to tries
* Exercise

### News / Etc.

* I've done the first read through of Monday's surveys.  There is not
  clear consensus.  Many people like the chance to think through problems.
  Many would like me to lecture more on the more difficult concepts.
  A few would like to code more in class.
* I was disappointed that none of you attended the CS Extra on Careers
  in Computing.  (Yes, I realize that it's a busy time.)
* I have not yet met with all the people involved in the issue we discussed
  on Monday.  When I've done so, I'll do my best to get exams back to you
  promptly.  (Note that I have not yet paired exams with people.)

### Upcoming work

* [Assignment 6](../assignments/assignment06) due Wednesday after
  break at 10:30 p.m.
* Read Skiena 3.9 (War Story: String 'em up)

### Extra credit (Academic)

* Aspen Trio at 7:30 p.m.
* CS Extras Thursday, UofI

### Extra credit (Peer)

* Today, 6:30 p.m. in Loose Yoni Ki Baat, women of color monologues

### Extra Credit (Misc)

### Other good things

### Questions

Background
----------

We've been looking at dictionaries.  You know many implementations.

* Associative arrays
* Association lists
* Search trees (balanced and unbalanced)
    * 2-3
    * Red-black
* Hash tables
    * With chaining <- people use
    * With probing <- sam learned
* Skip lists

Hash table are best if all you do is add/lookup.  O(1) expected amortized
time.

If you want additional features, such as "iterate in order", search trees
can be better.

We've lied.  Hash tables are not really O(1).  They are O(hashfun).  If
you are hashing n strings of length m, each hash takes O(m).

Introduction to tries
---------------------

Another implementation of dictionaries, this time focusing on strings as
the keys.  We will build a tree.  Each node will have ALPHA children,
where ALPHA is the size of the alphabet.

Our trees will "encode"/"store" keys by having an edge corresponding to
each letter of the word

Building a trie is straightforward: Follow the existing trie as far as
you can, then branch off.

There are subtleties.  For example, you may want to shrink long paths
to a single node with the edge a string, rather than a character.

Lookup takes O(|string|).  Add takes O(|string|).  We are trading numeric
computations (in hash tables) for pointer chasing (in tries).

Can we iterate the trie in order of keys from alphabetically first to
alphabetically last?

* Yes: Preorder, Depth-first, Left-to-right traversal

You are trading memory for speed and functionality.

Tries can be useful for other things, too.

HackerRank exercise
-------------------

<https://www.hackerrank.com/challenges/contacts/problem>

How would you get started?

* What strategy?
* How do you read the inputs and decide what to do?
* What does your data type look like?
* What procedures do you provide?

Some notes
----------

```
#include <stdio.h>
#include <string.h>
#include <math.h>
#include <stdlib.h>

// +-----------+-----------------------------------------------------
// | Constants |
// +-----------+

#define ALPHA 26

// +-------+---------------------------------------------------------
// | Types |
// +-------+

struct Trie {
    int count;                          // # descendants
    struct Trie *children[ALPHA];       // links to children
};

typedef struct Trie Trie;
typedef struct Trie TrieNode;


// +--------------------+--------------------------------------------
// | Utility Procedures |
// +--------------------+

/**
 * Create a new, empty, trie.
 */
Trie *
trie_new ()
{
  return (Trie *) 0;
} // trie_new

/**
 * Deallocate all the memory associated with a trie.
 */
void
trie_free (Trie * trie)
{
} // trie_free

/**
 * Add an element to the trie.
 * @pre: The element is not in the trie.
 */
void 
trie_add (Trie *trie, char *str)
{
    // fprintf (stderr, "Add %s\n", str);
} // add

/**
 * Look up a prefix in the trie.
 */
int
trie_lookup (Trie *trie, char *str)
{
    // fprintf (stderr, "Lookup %s\n", str);
    return 0;
} // lookup

// +------+----------------------------------------------------------
// | Main |
// +------+

int 
main() 
{
    
    int numlines;
    char command[5];
    char str[32];   // They say 21, but let's use a power of 2 for fun.
    Trie *trie = trie_new ();
    
    scanf ("%d", &numlines);
    for (int i = 0; i < numlines; i++)
    {
        scanf ("%s", command);
        scanf ("%s", str);
        if (strcmp (command, "add") == 0)
          trie_add (trie, str);
        else if (strcmp (command, "find") == 0)
          printf ("%d\n", trie_lookup (trie, str));
    }

    // Cleanup
    trie_free (trie);
    return 0;
} // main

```
