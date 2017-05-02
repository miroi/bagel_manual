.. _hf:

*************
Hartree--Fock
*************

Description
===========

SCF can be run using the following keywords

* Restricted HF for closed-shell systems: ``rhf`` or ``hf``
* Restricted open-shell HF: ``rohf``
* Unrestricted HF: ``uhf``

Except for restricted Hartree--Fock, density fitting is used by default. Density fitting basis has to be
specified in the Molecule block (see Molecule section).

RHF can be run with ECP basis sets and and fast multipole method (FMM). For RHF-FMM, ``"cfmm" : "true"``
has to be specified in the Molecule block (see Molecule section).

Keywords
========
The default values are recommended unless mentioned otherwise.

.. topic:: ``thresh`` or ``thresh_scf``

   | **Description**: SCF convergence threshold 
   | **Default**: 1.0e-8
   | **Datatype**: double

.. topic:: ``maxiter`` and ``maxiter_scf``

   | **Description**: number of iterations and number of SCF interations, which are the same if you only run SCF calculations
   | **Default**: 100
   | **Datatype**: integer 

.. topic:: ``diis_start`` and ``diis_size``

.. topic:: ``thresh_overlap``

   | **Description**: overlap integral threshold 
   | **Default**: 1.0e-8
   | **Datatype**: double

.. topic:: ``df`` (only for RHF) 

   | **Description**: use density fitting or not
   | **Default** : true (except for FMM)
   | **Datatype**: bool 

.. topic:: ``multipole``

   | **Description**: rank of multipole moments printed out
   | **Default** : 1 (dipoles)
   | **Values** : 1, 2
   | **Datatype**: integer 

.. topic:: ``dma``

   | **Description**: options to print out multipole moments from distributed multipole analysis
   | **Default** : 0 (not print out)
   | **Values** : 0, 1, 2, 3
   | **Datatype**: integer 


.. topic:: ``charge``

   | **Description**: molecular charge
   | **Default** : 0
   | **Datatype**: integer 

.. topic:: ``nact`` and ``nocc``

   | **Description**: number of unpaired electrons and occupied orbitals

.. topic:: ``restart``

   | **Description**: to restart the calculation from an archive file
   | **Default**: false
   | **Datatype**: bool

Keywords for RHF/FMM
====================

.. topic:: ``ns``

   | **Description**: level of descritization which controls the number of lowest-level boxes in one dimension for FMM
   | **Default**: 4 
   | **Datatype**: integer 

.. topic:: ``ws``

   | **Description**: well-separatedness index, which is the number of boxes that must separate
                      two collections of charges before they are considered distant 
                      and can interact through multipole expansions
   | **Default**: 2 
   | **Datatype**: integer 

.. topic:: ``lmax``

   | **Description**: order of the multipole expansions in FMM-J
   | **Default**: 10
   | **Datatype**: integer 

.. topic:: ``exchange``

   | **Description**: whether to include far-field exchange using occ-RI-FMM
   | **Default**: false
   | **Datatype**: integer 

.. topic:: ``lmax_exchange``

   | **Description**: order of the multipole expansions in FMM-K
   | **Default**: 2
   | **Datatype**: integer 

Examples
=======
Below are some examples for SCF calculations using RHF, ROHF, UHF, RHF with FMM.

RHF
---

.. code-block:: javascript 

   { "bagel" : [
   
   {
     "title" : "molecule",
     "basis" : "svp",
     "df_basis" : "svp_jkfit",
     "angstrom" : "false",
     "geometry" : [
       { "atom" : "F",  "xyz" : [ -0.000000,     -0.000000,      2.720616]},
       { "atom" : "H",  "xyz" : [ -0.000000,     -0.000000,      0.305956]}
     ]
   },
   
   {
     "title" : "hf",
     "df" : "true",
     "thresh" : 1.0e-8
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
     "thresh" : 1.0e-8
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
     "thresh" : 1.0e-8
   }
   
   ]}

RHF-FMM
-------
.. code-block:: javascript 

   { "bagel" : [
   
   {
     "title" : "molecule",
     "symmetry" : "C1",
     "basis" : "tzvpp",
     "angstrom" : "false",
     "cfmm" : "true",
     "geometry" : [
       { "atom" : "H", "xyz" : [  -97.770374233,    -91.172348950,   -466.211922530] },
       { "atom" : "F", "xyz" : [  -96.762432231,    -90.232427827,   -461.405614050] },
       { "atom" : "H", "xyz" : [  -66.524172159,    -62.034794131,   -317.216359660] },
       { "atom" : "F", "xyz" : [  -65.516230156,    -61.094873008,   -312.410051180] }
     ]
   },
   
   {
     "title" : "hf",
     "df" : "false",
     "ns" : "2",
     "ws" : "1",
     "lmax" : "10",
     "exchange" : "true",
     "lmax_exchange" : "2",
     "thresh" : 1.0e-8
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

