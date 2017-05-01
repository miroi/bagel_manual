.. _hf:

*************
Hartree--Fock
*************

Description
===========

.. math::
  H\Psi = E\Psi

Command: ``rhf`` or ``hf``

Prerequisite
=============
None

Keywords
========
The default values are recommended unless mentioned otherwise.

.. topic:: ``gradient``

   | Description: to compute gradient
   | Default: false
   | Datatype: bool
   | Recommendation: use default.

.. topic:: ``restart``

   | Description: to restart the calculation from an archive file
   | Default: false
   | Datatype: bool
   | Recommendation: use default.

.. topic:: ``maxiter``

   | Description: number of iterations
   | Default: 100
   | Datatype: integer 

.. topic:: ``maxiter`` and ``maxiter_scf``

   | Description: number of iterations and number of SCF interations, which are the same if you only run SCF calculations
   | Default: 100
   | Datatype: integer 

.. topic:: ``diis_start`` and ``diis_size``

.. topic:: ``thresh_overlap``

   | Description: overlap integral threshold 
   | Default: 1e-8
   | Datatype: double

.. topic:: ``thresh`` or ``thresh_scf``

   | Description: SCF convergence threshold 
   | Default: 1e-8
   | Datatype: double

Example
=======
This should be an example that is chemically relevant. There should be text explaining what the example is and why it's interesting.

RHF
---

.. code-block:: javascript 

   { "bagel" : [
   
   {
     "title" : "molecule",
     "symmetry" : "C2v",
     "basis" : "svp",
     "angstrom" : "false",
     "geometry" : [
       { "atom" : "F",  "xyz" : [ -0.000000,     -0.000000,      2.720616]},
       { "atom" : "H",  "xyz" : [ -0.000000,     -0.000000,      0.305956]}
     ]
   },
   
   {
     "title" : "hf",
     "df" : false,
     "thresh" : 1.0e-10
   }
   
   ]}

ROHF
----
.. code-block:: javascript 

   { "bagel" : [
   
   {
     "title" : "molecule",
     "symmetry" : "C1",
     "basis" : "svp",
     "df_basis" : "svp-jkfit",
     "angstrom" : "false",
     "geometry" : [
       { "atom" : "C",  "xyz" : [   -0.000000,     -0.000000,      3.000000] },
       { "atom" : "H",  "xyz" : [    0.000000,      0.000000,      0.000000] }
     ]
   },
   
   {
     "title" : "rohf",
     "nact" : 1,
     "thresh" : 1.0e-10
   }
   
   ]}

UHF
---
.. code-block:: javascript 

   { "bagel" : [
   
   {
     "title" : "molecule",
     "symmetry" : "C1",
     "basis" : "svp",
     "df_basis" : "svp-jkfit",
     "angstrom" : false,
     "geometry" : [
       { "atom" : "O",  "xyz" : [  -0.000000,     -0.000000,      1.500000]},
       { "atom" : "H",  "xyz" : [  -0.000000,     -0.000000,      0.000000]}
     ]
   },
   
   {
     "title" : "uhf",
     "nact" : 1,
     "thresh" : 1.0e-10
   }
   
   ]}

Some information about the output should also be included. This will not be entire output but enough for the reader to know their calculation worked.

References
==========

+-----------------------------------------------+-----------------------------------------------------------------------+
|          Description of Reference             |                          Reference                                    | 
+===============================================+=======================================================================+
| Reference was used for...                     | John Doe and Jane Doe. J. Chem. Phys. 1980, 5, 120-124.               |
+-----------------------------------------------+-----------------------------------------------------------------------+
| Reference was used for...                     | John Doe and Jane Doe. J. Chem. Phys. 1980, 5, 120-124.               |
+-----------------------------------------------+-----------------------------------------------------------------------+

