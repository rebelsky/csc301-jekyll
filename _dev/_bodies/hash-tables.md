Review of Hash Tables
---------------------

With your group

* What do you see as the key ideas behind hash tables?
* What ADT do hash tables implement?
* What design options are there in building hash tables?

Hash Functions
--------------

With your group

* What makes a good hash function?
* What does the following hash function do?

_Function borrowed from Skienna p. 89; expects arbitrary-precision integers_

    #define alpha SOME_LARGE_PRIME
    int hash(char *s)
    {
      int len = strlen(s);
      int code = 0;
      for (int i = 0; i < len; i++)
        {
          code += s[i] * expt(alpha, len-(i+1))
        } // for
      return code;
    } // hash


* Suppose we have a really long string.  What the difference between
  `hash(substring(str, 0, k))` and `hash(substring(str, 1, k+1))`?
* How would you rewrite this hash function to deal with the issue that
  integer values are capped?

Other Uses of Hash Tables and Functions
---------------------------------------

_Ideas stolen from Skiena_

How could you use hash functions or tables to help you ...

* Determine if string `a` is a substring of string `b`?
* Detect plagiarism
