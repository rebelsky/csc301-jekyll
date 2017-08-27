Variants of string matching
---------------------------

* General: Find a pattern string in a target string.
* Variant: Do we match exactly or approximately?
* Variant: Do we search for a single string or multiple strings?
* Variant: Do we find the first location or all locations?

Approximate string matching, revisited
--------------------------------------

* How would we change the dynamic programming algorithm to find
  a substring?

Matching multiple strings
-------------------------

* What algorithms do you know for matching multiple substrings (e.g.,
  finding each position of each substring)?
* What's the running time?
    * Source string is length n.
    * There are k pattern strings, each of length m.
* One algorithm we know is Rabin-Karp, which we discussed during
  our discussion of hashing..

Substring matching, revisited
-----------------------------

* Can we write a single substring matching algorithm that looks at each
  character in the source string at most once, perhaps by doing some
  preprocessing of the pattern string?
