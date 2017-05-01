.. _gradient:

********
Gradient
********

Description
===========
Computes the nuclear gradient.

Pre-requisite
=============
Reference wave function (such as HF).

Keywords
========
.. topic:: ``title``

   | **Description:** The title of the type of gradient calculation being performed. 
   | **Default:** N/A 
   | **Datatype:** string 
   | **Values:** (force, nacme, dgrad)
   |    ``force``: Calculates the gradient (force)
   |    ``nacme``: Calculates the non-adiabatic coupling matrix elements
   |    ``dgrad``: Difference gradient (only available for CASSCF)
   | **Recommendation:** N/A

.. topic:: ``method``

   | **Description:** The method to be used for energy evaluation 
   | **Default:** N/A 
   | **Datatype:** string 
   | **Values:**
   |    ``UHF``: Unrestricted Hartree Fock 
   |    ``ROHF``: Restricted Open-shell Hartree Fock
   |    ``HF``: Restricted Hartree Fock
   |    ``DHF`` : Dirac Hartree Fock
   |    ``MP2`` : Moller Plesset Perturbation Theory
   |    ``CASSCF`` : Complete Active Space Self Consistent Field (CASSCF)
   |    ``CASPT2`` : Complete Active Space SCF with Secont Order Perturbation Theory (CASPT2) 
   | **Recommendation:** N/A


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

