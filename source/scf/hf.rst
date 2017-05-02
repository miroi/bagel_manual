.. index:: scf, hf, rhf, uhf, rohf, soscf, cfmm

.. _hf:

*************
Hartree--Fock
*************

Description
===========

SCF can be run by specifying the following values to the keyword ``title``:

* Restricted HF for closed-shell systems: ``rhf`` or ``hf``
* Restricted open-shell HF: ``rohf``
* Unrestricted HF: ``uhf``
* Two-component HF using ECP basis sets: ``soscf``

Except for restricted Hartree--Fock, density fitting is used by default. Density fitting basis has to be
specified in the Molecule block (see :ref:`molecule` section).

RHF can be run with fast multipole method (FMM). For RHF-FMM, ``"cfmm" : "true"``
has to be specified in the molecule block (see :ref:`molecule` section).

Keywords
========
The default values are recommended unless mentioned otherwise.

.. topic:: ``thresh``

   | **Description**: SCF convergence threshold for the root-mean-squared of the error vector.
   | **Default**: :math:`1.0\times 10^{-8}`
   | **Datatype**: double

.. topic:: ``maxiter``/``maxiter_scf``

   | **Description**: number of iterations and number of SCF interations, after which the program will terminate if convergence is not reached.
   | **Default**: :math:`100`
   | **Datatype**: int 

.. topic:: ``diis_start``

   | **Description**: after the specified iteration, we will begin using Pulay’s Direct Inversion in the Iterative Subspace (DIIS)
                      algorithm for the to update the orbitals.
   | **Default**: :math:`1`
   | **Datatype**: int 


.. topic:: ``thresh_overlap``

   | **Description**: Overlap threshold used to identify linear dependancy in the atomic basis set.
                      Increasing this value will more aggressively remove linearly dependent basis vectors.
   | **Default**: :math:`1.0\times 10^{-8}`
   | **Datatype**: double

.. topic:: ``multipole``

   | **Description**: rank of Cartesian multipole moments printed out.
   | **Default** : :math:`1` (dipoles)
   | **Values** : :math:`1, 2`
   | **Datatype**: int 

.. topic:: ``dma``

   | **Description**: options to print out multipole moments from distributed multipole analysis.
   | **Default** : :math:`0` (not print out)
   | **Values** : :math:`0, 1, 2, 3`
   | **Datatype**: int 


.. topic:: ``charge``

   | **Description**: molecular charge
   | **Default** : :math:`0`
   | **Datatype**: int 

.. topic:: ``nopen``

   | **Description**: number of unpaired electrons in high-spin unrestricted Hartree--Fock
   | **Default** : (number of electrons - charge) % 2
   | **Datatype** : int

.. topic:: ``restart``

   | **Description**: to restart the calculation from an archive file
   | **Default**: false
   | **Datatype**: bool

Keywords for RHF-FMM
====================

.. topic:: ``ns``

   | **Description**: level of descritization which controls the number of lowest-level boxes in one dimension for FMM
   | **Default**: :math:`4`
   | **Datatype**: int 

.. topic:: ``ws``

   | **Description**: well-separatedness index, which is the number of boxes that must separate
                      two collections of charges before they are considered distant 
                      and can interact through multipole expansions
   | **Default**: :math:`2`
   | **Datatype**: int 

.. topic:: ``lmax``

   | **Description**: order of the multipole expansions in FMM-J
   | **Default**: :math:`10`
   | **Datatype**: int 

.. topic:: ``exchange``

   | **Description**: whether to include far-field exchange using occ-RI-FMM
   | **Default**: false
   | **Datatype**: int 

.. topic:: ``lmax_exchange``

   | **Description**: order of the multipole expansions in FMM-K
   | **Default**: :math:`2`
   | **Datatype**: int 

.. topic:: ``fmm_thresh``

   | **Description**: integral screening threshold used in FMM
   | **Default**: ``thresh_overlap``
   | **Datatype**: double 

Examples
========
Below are some examples for SCF calculations using RHF, ROHF, UHF, SOSCF, and RHF-FMM.

RHF
---

.. code-block:: javascript 

   { "bagel" : [
   
   {
     "title" : "molecule",
     "basis" : "svp",
     "df_basis" : "svp-jkfit",
     "angstrom" : "false",
     "geometry" : [
       { "atom" : "F",  "xyz" : [ -0.000000,     -0.000000,      2.720616]},
       { "atom" : "H",  "xyz" : [ -0.000000,     -0.000000,      0.305956]}
     ]
   },
   
   {
     "title" : "hf",
     "thresh" : 1.0e-8
   }
   
   ]}

The converged SCF energy is :math:`-99.84772354` after :math:`11` iterations.

ROHF
----
.. code-block:: javascript 

   { "bagel" : [
   
   {
     "title" : "molecule",
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

The converged SCF energy is :math:`-38.16810629` after :math:`11` iterations.

UHF
---
.. code-block:: javascript 

   { "bagel" : [
   
   {
     "title" : "molecule",
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

The converged SCF energy is :math:`-75.28410147` after :math:`12` iterations.

SOSCF
-----

.. code-block:: javascript 

   { "bagel" : [
   
   {
     "title" : "molecule",
     "basis" : "ecp28mdf",
     "df_basis" : "tzvpp-jkfit",
     "angstrom" : "true",
     "geometry" : [
       { "atom" : "Br",  "xyz" : [  0.000000,      0.000000,      0.000000]},
       { "atom" :  "H",  "xyz" : [  0.000000,      1.420000,      0.000000],
                        "basis" : "sto-3g"}
     ]
   },
   
   {
     "title" : "soscf",
     "thresh" : 1.0e-8
   }
   
   ]}

RHF-FMM
-------
.. figure:: hf-graphene.png
    :width: 300px
    :align: center
    :alt: alternate text
    :figclass: align-center


.. code-block:: javascript 

   { "bagel" : [
   
   {
     "title" : "molecule",
     "basis" : "/home/le/develop/bagel/src/basis/3-21g.json",
     "angstrom" : "true",
     "cfmm" : "true",
     "schwarz_thresh" : "1.0e-8",
     "geometry" : [
       { "atom" : "C", "xyz" : [     -0.710000000,    1.229756073,    0.000000000] },
       { "atom" : "C", "xyz" : [      0.710000000,    1.229756073,    0.000000000] },
       { "atom" : "C", "xyz" : [      1.420000000,    0.000000000,    0.000000000] },
       { "atom" : "C", "xyz" : [      0.710000000,   -1.229756073,    0.000000000] },
       { "atom" : "C", "xyz" : [     -0.710000000,   -1.229756073,    0.000000000] },
       { "atom" : "C", "xyz" : [     -1.420000000,    0.000000000,    0.000000000] },
       { "atom" : "C", "xyz" : [     -7.810000000,    1.229756073,    0.000000000] },
       { "atom" : "C", "xyz" : [     -7.100000000,    0.000000000,    0.000000000] },
       { "atom" : "C", "xyz" : [      7.810000000,   -1.229756073,    0.000000000] },
       { "atom" : "C", "xyz" : [     -7.810000000,    3.689268220,    0.000000000] },
       { "atom" : "C", "xyz" : [     -7.100000000,    2.459512147,    0.000000000] },
       { "atom" : "C", "xyz" : [      7.810000000,   -3.689268220,    0.000000000] },
       { "atom" : "C", "xyz" : [      7.100000000,   -2.459512147,    0.000000000] },
       { "atom" : "C", "xyz" : [     -7.100000000,    4.919024293,    0.000000000] },
       { "atom" : "C", "xyz" : [     -7.100000000,   -4.919024293,    0.000000000] },
       { "atom" : "C", "xyz" : [     -3.550000000,    1.229756073,    0.000000000] },
       { "atom" : "C", "xyz" : [     -2.840000000,    0.000000000,    0.000000000] },
       { "atom" : "C", "xyz" : [      3.550000000,   -1.229756073,    0.000000000] },
       { "atom" : "C", "xyz" : [     -4.970000000,    1.229756073,    0.000000000] },
       { "atom" : "C", "xyz" : [     -5.680000000,    0.000000000,    0.000000000] },
       { "atom" : "C", "xyz" : [      4.970000000,   -1.229756073,    0.000000000] },
       { "atom" : "C", "xyz" : [     -3.550000000,    3.689268220,    0.000000000] },
       { "atom" : "C", "xyz" : [     -2.840000000,    2.459512147,    0.000000000] },
       { "atom" : "C", "xyz" : [      3.550000000,   -3.689268220,    0.000000000] },
       { "atom" : "C", "xyz" : [      2.840000000,   -2.459512147,    0.000000000] },
       { "atom" : "C", "xyz" : [     -4.970000000,    3.689268220,    0.000000000] },
       { "atom" : "C", "xyz" : [     -5.680000000,    2.459512147,    0.000000000] },
       { "atom" : "C", "xyz" : [      4.970000000,   -3.689268220,    0.000000000] },
       { "atom" : "C", "xyz" : [      5.680000000,   -2.459512147,    0.000000000] },
       { "atom" : "C", "xyz" : [     -3.550000000,    6.148780367,    0.000000000] },
       { "atom" : "C", "xyz" : [     -2.840000000,    4.919024293,    0.000000000] },
       { "atom" : "C", "xyz" : [      3.550000000,   -6.148780367,    0.000000000] },
       { "atom" : "C", "xyz" : [      2.840000000,   -4.919024293,    0.000000000] },
       { "atom" : "C", "xyz" : [     -4.970000000,    6.148780367,    0.000000000] },
       { "atom" : "C", "xyz" : [     -5.680000000,    4.919024293,    0.000000000] },
       { "atom" : "C", "xyz" : [      4.970000000,   -6.148780367,    0.000000000] },
       { "atom" : "C", "xyz" : [      5.680000000,   -4.919024293,    0.000000000] },
       { "atom" : "C", "xyz" : [     -2.840000000,    7.378536440,    0.000000000] },
       { "atom" : "C", "xyz" : [     -2.840000000,   -7.378536440,    0.000000000] },
       { "atom" : "C", "xyz" : [      0.710000000,    3.689268220,    0.000000000] },
       { "atom" : "C", "xyz" : [      1.420000000,    2.459512147,    0.000000000] },
       { "atom" : "C", "xyz" : [     -0.710000000,   -3.689268220,    0.000000000] },
       { "atom" : "C", "xyz" : [     -1.420000000,   -2.459512147,    0.000000000] },
       { "atom" : "C", "xyz" : [     -0.710000000,    3.689268220,    0.000000000] },
       { "atom" : "C", "xyz" : [     -1.420000000,    2.459512147,    0.000000000] },
       { "atom" : "C", "xyz" : [      0.710000000,   -3.689268220,    0.000000000] },
       { "atom" : "C", "xyz" : [      1.420000000,   -2.459512147,    0.000000000] },
       { "atom" : "C", "xyz" : [      0.710000000,    6.148780367,    0.000000000] },
       { "atom" : "C", "xyz" : [      1.420000000,    4.919024293,    0.000000000] },
       { "atom" : "C", "xyz" : [     -0.710000000,   -6.148780367,    0.000000000] },
       { "atom" : "C", "xyz" : [     -1.420000000,   -4.919024293,    0.000000000] },
       { "atom" : "C", "xyz" : [     -0.710000000,    6.148780367,    0.000000000] },
       { "atom" : "C", "xyz" : [     -1.420000000,    4.919024293,    0.000000000] },
       { "atom" : "C", "xyz" : [      0.710000000,   -6.148780367,    0.000000000] },
       { "atom" : "C", "xyz" : [      1.420000000,   -4.919024293,    0.000000000] },
       { "atom" : "C", "xyz" : [      0.710000000,    8.608292514,    0.000000000] },
       { "atom" : "C", "xyz" : [      1.420000000,    7.378536440,    0.000000000] },
       { "atom" : "C", "xyz" : [     -0.710000000,   -8.608292514,    0.000000000] },
       { "atom" : "C", "xyz" : [     -1.420000000,   -7.378536440,    0.000000000] },
       { "atom" : "C", "xyz" : [     -0.710000000,    8.608292514,    0.000000000] },
       { "atom" : "C", "xyz" : [     -1.420000000,    7.378536440,    0.000000000] },
       { "atom" : "C", "xyz" : [      0.710000000,   -8.608292514,    0.000000000] },
       { "atom" : "C", "xyz" : [      1.420000000,   -7.378536440,    0.000000000] },
       { "atom" : "C", "xyz" : [      4.970000000,    1.229756073,    0.000000000] },
       { "atom" : "C", "xyz" : [      5.680000000,    0.000000000,    0.000000000] },
       { "atom" : "C", "xyz" : [     -4.970000000,   -1.229756073,    0.000000000] },
       { "atom" : "C", "xyz" : [      3.550000000,    1.229756073,    0.000000000] },
       { "atom" : "C", "xyz" : [      2.840000000,    0.000000000,    0.000000000] },
       { "atom" : "C", "xyz" : [     -3.550000000,   -1.229756073,    0.000000000] },
       { "atom" : "C", "xyz" : [      4.970000000,    3.689268220,    0.000000000] },
       { "atom" : "C", "xyz" : [      5.680000000,    2.459512147,    0.000000000] },
       { "atom" : "C", "xyz" : [     -4.970000000,   -3.689268220,    0.000000000] },
       { "atom" : "C", "xyz" : [     -5.680000000,   -2.459512147,    0.000000000] },
       { "atom" : "C", "xyz" : [      3.550000000,    3.689268220,    0.000000000] },
       { "atom" : "C", "xyz" : [      2.840000000,    2.459512147,    0.000000000] },
       { "atom" : "C", "xyz" : [     -3.550000000,   -3.689268220,    0.000000000] },
       { "atom" : "C", "xyz" : [     -2.840000000,   -2.459512147,    0.000000000] },
       { "atom" : "C", "xyz" : [      4.970000000,    6.148780367,    0.000000000] },
       { "atom" : "C", "xyz" : [      5.680000000,    4.919024293,    0.000000000] },
       { "atom" : "C", "xyz" : [     -4.970000000,   -6.148780367,    0.000000000] },
       { "atom" : "C", "xyz" : [     -5.680000000,   -4.919024293,    0.000000000] },
       { "atom" : "C", "xyz" : [      3.550000000,    6.148780367,    0.000000000] },
       { "atom" : "C", "xyz" : [      2.840000000,    4.919024293,    0.000000000] },
       { "atom" : "C", "xyz" : [     -3.550000000,   -6.148780367,    0.000000000] },
       { "atom" : "C", "xyz" : [     -2.840000000,   -4.919024293,    0.000000000] },
       { "atom" : "C", "xyz" : [      2.840000000,    7.378536440,    0.000000000] },
       { "atom" : "C", "xyz" : [      2.840000000,   -7.378536440,    0.000000000] },
       { "atom" : "C", "xyz" : [      7.810000000,    1.229756073,    0.000000000] },
       { "atom" : "C", "xyz" : [      7.100000000,    0.000000000,    0.000000000] },
       { "atom" : "C", "xyz" : [     -7.810000000,   -1.229756073,    0.000000000] },
       { "atom" : "C", "xyz" : [      7.810000000,    3.689268220,    0.000000000] },
       { "atom" : "C", "xyz" : [      7.100000000,    2.459512147,    0.000000000] },
       { "atom" : "C", "xyz" : [     -7.810000000,   -3.689268220,    0.000000000] },
       { "atom" : "C", "xyz" : [     -7.100000000,   -2.459512147,    0.000000000] },
       { "atom" : "C", "xyz" : [      7.100000000,    4.919024293,    0.000000000] },
       { "atom" : "C", "xyz" : [      7.100000000,   -4.919024293,    0.000000000] },
       { "atom" : "H", "xyz" : [      1.250000000,    9.543599950,    0.000000000] },
       { "atom" : "H", "xyz" : [     -1.250000000,   -9.543599950,    0.000000000] },
       { "atom" : "H", "xyz" : [      5.510000000,    7.084087803,    0.000000000] },
       { "atom" : "H", "xyz" : [     -5.510000000,   -7.084087803,    0.000000000] },
       { "atom" : "H", "xyz" : [      3.380000000,    8.313843876,    0.000000000] },
       { "atom" : "H", "xyz" : [      3.380000000,   -8.313843876,    0.000000000] },
       { "atom" : "H", "xyz" : [      7.640000000,    5.854331730,    0.000000000] },
       { "atom" : "H", "xyz" : [      7.640000000,   -5.854331730,    0.000000000] },
       { "atom" : "H", "xyz" : [     -7.640000000,    5.854331730,    0.000000000] },
       { "atom" : "H", "xyz" : [     -7.640000000,   -5.854331730,    0.000000000] },
       { "atom" : "H", "xyz" : [     -5.510000000,    7.084087803,    0.000000000] },
       { "atom" : "H", "xyz" : [      5.510000000,   -7.084087803,    0.000000000] },
       { "atom" : "H", "xyz" : [     -3.380000000,    8.313843876,    0.000000000] },
       { "atom" : "H", "xyz" : [     -3.380000000,   -8.313843876,    0.000000000] },
       { "atom" : "H", "xyz" : [     -1.250000000,    9.543599950,    0.000000000] },
       { "atom" : "H", "xyz" : [      1.250000000,   -9.543599950,    0.000000000] },
       { "atom" : "H", "xyz" : [      8.890000000,    1.229756073,    0.000000000] },
       { "atom" : "H", "xyz" : [     -8.890000000,   -1.229756073,    0.000000000] },
       { "atom" : "H", "xyz" : [      8.890000000,    3.689268220,    0.000000000] },
       { "atom" : "H", "xyz" : [     -8.890000000,   -3.689268220,    0.000000000] },
       { "atom" : "H", "xyz" : [     -8.890000000,    1.229756073,    0.000000000] },
       { "atom" : "H", "xyz" : [      8.890000000,   -1.229756073,    0.000000000] },
       { "atom" : "H", "xyz" : [     -8.890000000,    3.689268220,    0.000000000] },
       { "atom" : "H", "xyz" : [      8.890000000,   -3.689268220,    0.000000000] }
     ]
   },
   
   {
     "df" : false,
     "ns" : "4",
     "lmax" : "10",
     "ws" : "0.5",
     "thresh_fmm" : "1.0e-12",
     "exchange" : true,
     "lmax_exchange" : "2",
     "title" : "hf",
     "thresh" : 1.0e-6
   }
   
   ]}

References
==========
BAGEL Reference
---------------

+-----------------------------------------------+----------------------------------------------------------------------------+
|          Description of Reference             |                               Reference                                    | 
+===============================================+============================================================================+
| Exact exchange evaluation using occ-RI-FMM    | H\.-A. Le, and T. Shiozaki, in preparation                                 |
+-----------------------------------------------+----------------------------------------------------------------------------+

General Reference
-----------------
+-----------------------------------------------+----------------------------------------------------------------------------+
|          Description of Reference             |                               Reference                                    | 
+===============================================+============================================================================+
| General text on electronic structure theory   | A\. Szabo, and N. S. Ostlund, Modern Quantum Chemistry: Introduction to    |
|                                               | Advanced Electronic Structure Theory, Dover Publications                   |
+-----------------------------------------------+----------------------------------------------------------------------------+
| References for fast multipole method in       | C\. A. White, B. G. Johnson, P. M. W. Gill, and M. Head-Gordon,            |
| quantum chemistry                             | Chem. Phys. Lett. **230**, 8 (1994)                                        |
+-----------------------------------------------+----------------------------------------------------------------------------+
|                                               | M\. C. Strain, G. E. Scuseria, and M. J. Frisch, Science **271**, 51 (1996)|
+-----------------------------------------------+----------------------------------------------------------------------------+

