Matching multiple strings
-------------------------

* What algorithms do you know for matching multiple substrings (e.g.,
  finding each position of each substring)?
* What's the running time?
    * text is length n.
    * There are k patterns, each of length m.
* One algorithm we know is Rabin-Karp, which we discussed during
  our discussion of hashing..

Substring matching, revisited
-----------------------------

* Can we write a single substring matching algorithm that reads
  each character in the text at most once, perhaps by doing
  some preprocessing of the pattern string?
* Why?  Perhaps we have a limited buffer and we're reading from somewhertext
  else?  Perhaps because we know that sensible use of the i
* Example 1
    * pattern: aaab
    * text: aaaaaaab
* Example 2
    * pattern: abcabcabd
    * text: abcabcabcabdbc
* Example 3 (due to Knuth, Morris, Pratt)
    * pattern: abcabcacab
    * text: babcabcabcaabcabcabcacabc
* We should find that we'll end up with a model of "re-placing" the
  pattern.
