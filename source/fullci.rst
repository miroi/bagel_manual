.. _fullci:

*******
Full CI
*******

Description
===========
Full CI diagonalizes Full CI Hamiltonian.

Example
=======
[ { bagel, … } ]

Pre-requisite
=============
Reference wave function (such as HF).

Keywords
========
Frozen
------
| DESCRIPTION: to have frozen orbital or not.
|   DEFAULT: false.
|   DATATYPE: bool
|   VALUES:
|     TRUE: DESCRIPTION: have frozen orbital.
|     FALSE: DESCRIPTION: do not have frozen orbital.
|   RECOMMENDATION: use default.
Algorithm
---------
| DESCRIPTION: full CI algorithm.
|   DEFAULT: kh.
|   DATATYPE: string
|   VALUES: 
|     KH, Knowles, Handy: DESCRIPTION: use Knowles—Handy.
|     HZ, Harrison, Zarrabian: DESCRIPTION: use Harrison—Zarrabian.
|     Dist: DESCRIPTION: use Parallel algorithm.
|   RECOMMENDATION: if the active space is large and you have multiple processes, use Dist. Otherwise, use default.

.. math:: (a + b)^2 = a^2 + 2ab + b^2
.. math::
 :nowrap:

   \begin{eqnarray}
      y    & = & ax^2 + bx + c \\
      f(x) & = & x^2 + 2xy + y^2
   \end{eqnarray}

.. math::
  H\Psi = E\Psi

Example
=======
This should be an example that is chemically relevant. There should be text explaining what the example is and why it's interesting.

.. code-block:: javascript 

   { "bagel" : [

   {
     "title" : "molecule",
     "basis" : "sto-3g",
     "df_basis" : "svp-jkfit",
     "angstrom" : false,
     "geometry" : [
       { "atom" : "F",  "xyz" : [   -0.000000,     -0.000000,      2.720616]},
       { "atom" : "H",  "xyz" : [   -0.000000,     -0.000000,      0.305956]}
     ]
   },

   {
     "title" : "hf",
     "thresh" : 1.0e-10
   },

   {
     "title" : "fci",
     "algorithm" : "parallel",
     "nstate" : 2
   }

   ]}


Some information about the output should also be included. This will not be entire output but enough for the reader to know their calculation worked.

.. figure:: figure/example.png
    :width: 200px
    :align: center
    :alt: alternate text
    :figclass: align-center

    This is an example of how to insert a figure. 

References
==========

+-----------------------------------------------+-----------------------------------------------------------------------+
|          Description of Reference             |                          Reference                                    | 
+===============================================+=======================================================================+
| Reference was used for...                     | John Doe and Jane Doe. J. Chem. Phys. 1980, 5, 120-124.               |
+-----------------------------------------------+-----------------------------------------------------------------------+
| Reference was used for...                     | John Doe and Jane Doe. J. Chem. Phys. 1980, 5, 120-124.               |
+-----------------------------------------------+-----------------------------------------------------------------------+

