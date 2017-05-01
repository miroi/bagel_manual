.. _nevpt2:

*******
NEVPT2
*******


Description
===========
Description here

.. math::
  insert formula here


Keywords
========

.. topic:: ``frozen``

   | DESCRIPTION: to have frozen orbitals or not.
   | DEFAULT: true
   | DATATYPE: bool

.. topic:: ``ncore``
   
   | DESCRIPTION: manually specify number of frozen orbitals, used when 'frozen' is turned on.
   | DATATYPE: int

.. topic:: ``aux_basis``
   
   | DESCRIPTION: specify an alternative density fitting basis set.
   | DEFAULT: use the same density fitting basis as in molecule/df_basis.
   | DATATYPE: string


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

