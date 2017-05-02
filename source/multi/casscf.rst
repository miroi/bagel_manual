.. _casscf:

****************************************************
Complete active space self-consistent field (CASSCF)
****************************************************

Description
===========

CASSCF simultaneously optimizes the orbital coefficients and the CI coefficients of all the possible determinants generated from the active space.
The state-averaging scheme for calculating excited states is also implemented.

The second-order algorithm is implemented in BAGEL. This algorithm is constructed of macroiterations and microiterations. At each macroiteration,
the CI coefficient is optimized by FCI calculations, while the orbitals are rotated in microiterations. 

Command: ``casscf``

Keywords
========

.. topic:: ``nstate``

   | **Description:** Number of states included in the state averaging.
   | **Default:** 1.
   | **Datatype:** integer

.. topic:: ``nact``

   | **Description:** Number of active orbitals.
   | **Default:** 0.
   | **Datatype:** integer

.. topic:: ``nclosed``

   | **Description:** Number of closed orbitals.
   | **Default:** Number of electrons / 2.
   | **Datatype:** integer

.. topic:: ``active``

   | **Description:** Specify active orbitals. Note that the orbital index starts from 1.
   | **Default:** Nact / 2 orbitals lower and higher from the valence orbital.
   | **Example:**
   |    [36, 37, 39] : include 36th, 37th, and 39th orbitals.
   | **Datatype:** integer array

.. topic:: ``algorithm``

   | **Description:** Orbital optimization algorithm.
   | **Default:** ``second``
   | **Datatype:** string
   | **Values:**
   |    ``second``: second-order algorithm.
   |    ``noopt``: no orbital optimization.
   | **Recommendation:** use default.

.. topic:: ``fci_algorithm``

   | **Description:** FCI algorithm employed in each macroiteration.
   | **Default:** ``parallel`` (when the number of active orbital is larger than 9 and number of process is larger than 8), ``knowles`` (otherwise)
   | **Datatype:** string
   | **Values:**
   |    ``knowles``, ``handy``, ``kh``: Knowles--Handy Algorithm.
   |    ``harrison``, ``zarrabian``, ``hz``: Harrison--Zarrabian Algorithm.
   |    ``parallel``, ``dist``: Parallel FCI algorithm.
   | **Recommendation:** use default.

.. topic:: ``thresh``

   | **Description:** Convergence threshold in macroiteration.
   | **Default:** 1.0e-8.
   | **Datatype:** double precision
   | **Recommendation:** use default.

.. topic:: ``thresh_micro``

   | **Description:** Convergence threshold in microiteration.
   | **Default:** 5.0e-6.
   | **Datatype:** double precision
   | **Recommendation:** use default.

.. topic:: ``conv_ignore``

   | **Description:** Throw the calculation or not when the convergence is not reached.
   | **Default:** false.
   | **Datatype:** bool
   | **Values:**
   |    ``true``: Do not throw the calculation.
   |    ``false``: Throw the calculation.
   | **Recommendation:** use default.

.. topic:: ``natocc``

   | **Description:** Print natural orbitals or not.
   | **Default:** false.
   | **Datatype:** bool
   | **Values:**
   |    ``true``: Print natural orbitals.
   |    ``false``: Do not print natural orbitals.
   | **Recommendation:** use default.

.. topic:: ``maxiter``

   | **Description:** Maximum number of macroiteration.
   | **Default:** 50.
   | **Datatype:** integer
   | **Recommendation:** Increase if convergence is not obtained.

.. topic:: ``maxiter_micro``

   | **Description:** Maximum number of microiteration.
   | **Default:** 100.
   | **Datatype:** integer
   | **Recommendation:** use default.

Example
=======

Sample input
------------


References
==========

+-----------------------------------------------+------------------------------------------------------------------------------------------------+
|          Description of Reference             |                          Reference                                                             | 
+===============================================+================================================================================================+
| Second-order orbital optimization             | H\.-J. Werner, Adv. Chem. Phys. 69, 1 (1987).                                                  |
+-----------------------------------------------+------------------------------------------------------------------------------------------------+

