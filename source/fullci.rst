.. _fullci:

***************
METHOD: Full CI
***************
DESCRIPTION: Full CI diagonalizes Full CI Hamiltonian.
EXAMPLE: [ { bagel, … } ]
PRE-REQUISITE: Reference wave function (such as HF).
KEYWORDS:
Frozen: DESCRIPTION: to have frozen orbital or not.
  DEFAULT: false.
  DATATYPE: bool
  VALUES:
    TRUE: DESCRIPTION: have frozen orbital.
    FALSE: DESCRIPTION: do not have frozen orbital.
  RECOMMENDATION: use default.
Algorithm:  DESCRIPTION: full CI algorithm.
  DEFAULT: kh.
  DATATYPE: string
  VALUES: 
    KH, Knowles, Handy: DESCRIPTION: use Knowles—Handy.
    HZ, Harrison, Zarrabian: DESCRIPTION: use Harrison—Zarrabian.
    Dist: DESCRIPTION: use Parallel algorithm.
  RECOMMENDATION: if the active space is large and you have multiple processes, use Dist. Otherwise, use default.
