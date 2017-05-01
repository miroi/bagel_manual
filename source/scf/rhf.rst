.. _scf:

*******
SCF
*******

Description
===========
Full CI diagonalizes Full CI Hamiltonian.

.. math::
  H\Psi = E\Psi

Pre-requisite
=============
Reference wave function (such as HF).

Keywords
========
.. topic:: ``frozen``

   | DESCRIPTION: to have frozen orbital or not.
   | DEFAULT: false.
   | DATATYPE: bool
   | VALUES:
   |    ``TRUE``: have frozen orbital.
   |    ``FALSE``: do not have frozen orbital.
   | RECOMMENDATION: use default.

.. topic:: ``algorithm``

   | DESCRIPTION: full CI algorithm.
   | DEFAULT: kh.
   | DATATYPE: string
   | VALUES: 
   |    ``KH, Knowles, Handy``: use Knowles—Handy.
   |    ``HZ, Harrison, Zarrabian``: use Harrison—Zarrabian.
   |    ``Dist``: use Parallel algorithm.
   | RECOMMENDATION: if the active space is large and you have multiple processes, use Dist. Otherwise, use default.


Example
=======
This should be an example that is chemically relevant. There should be text explaining what the example is and why it's interesting.

Sample input
------------

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

