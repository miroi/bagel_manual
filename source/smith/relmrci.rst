.. _relmrci:

***************************************************************
Relativistic Multireference configuration interaction (RelMRCI)
***************************************************************


Description
===========
Relativistic version of the fully internally contracted multireference configuration interaction.
This is implemented with the automatical code generator SMITH3.
By default, the Davidson corrected (+Q) energy is also printed.

Keywords
========
CASSCF keywords
---------------
See :ref:`casscf`.

SMITH keywords
--------------

.. topic:: ``thresh``

   | **Description:** Convergence threshold.
   | **Default:** 1.0e-8 (gradient) 1.0e-6 (otherwise)
   | **Datatype:** double precision
   | **Recommendation:** use default.

.. topic:: ``thresh_overlap``

   | **Description:** Overlap threshold.
   | **Default:** 1.0-9
   | **Datatype:** double precision
   | **Recommendation:** use default.

.. topic:: ``frozen``

   | **Description:** Have frozen orbitals or not.
   | **Default:** true.
   | **Datatype:** bool
   | **Values:**
   |    ``true``: use frozen orbitals.
   |    ``false``: do without frozen orbitals.
   | **Recommendation:** use default.

.. topic:: ``maxiter``

   | **Description:** Maximum number of iterations in MRCI calculations.
   | **Default:** 50
   | **Datatype:** integer
   | **Recommendation:** use default.

.. topic:: ``maxtile``

   | **Description:** Maximum number of orbitals in a single data tile used in SMITH3.
   | **Default:** 10
   | **Datatype:** integer
   | **Recommendation:** use default.


Example
=======

References
==========

+---------------------------------------------------+--------------------------------------------------------------------------------------+
|          Description of Reference                 |                          Reference                                                   | 
+===================================================+======================================================================================+
|  Fully internally contracted (Rel)MRCI            | T\. Shiozaki, and W. Mizukami, J. Chem. Theory Comput. **11**, 4733 (2015)           |
+---------------------------------------------------+--------------------------------------------------------------------------------------+

