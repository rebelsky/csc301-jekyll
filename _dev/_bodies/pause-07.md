Prefix Tables, Revisited
------------------------

We have decided that we can do pattern matching more efficiently if
we have a table that tells us how much of the pattern we can still
note that we've matched when we hit a non-matching character.

Example

    pattern: a a a a b
    preserve:0 0 0 0 3

We decided we should try to build our own tables.

    pattern: a b a b a c
    preserve:

    pattern: a b a c a b
    preserve:

    pattern: a b c a b d a a b
    preserve:

    pattern: a b c a b c a c a b  (from KMP)
    preserve: 

The Knuth-Morris-Pratt Algorithm
--------------------------------

    Inputs:
      text, a string
      pattern, a string
      P, the table described above
    Steps:     
      i = 0; // Index into text
      j = 0; // Index into pattern
      while (i < length(text) - length(pattern))
        if (text[i] == pattern[j])
          ++i;
          ++j;
        else if j == 0
          ++i;
        else
          j = P[j]

Building the KNP Table
----------------------

Easy approach: Build a table that gives how much of the prefix we've matched,
use that along the way.
