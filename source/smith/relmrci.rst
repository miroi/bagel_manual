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

.. topic:: ``title``

   | **Description:** Method to use in SMITH-generated code.
   | **Default:** N/A.
   | **Datatype:** string
   | **Values:**
   |    ``caspt2``: Request (Rel)CASPT2 calculation.
   |    ``mrci``: Request (Rel)MRCI calculation.
   |    ``casa``: Request (Rel)CAS/A calculation.

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

.. topic:: ``ncore``

   | **Description:** Number of frozen core orbitals.
   | **Default:** If ``frozen`` is true, then the number of core orbitals (first period, 2 per atom, second - third period, 8 per atom, ...).
   | **Datatype:** integer
   | **Recommendation:** Use default.

.. topic:: ``nfrozenvirt``

   | **Description:** Number of frozen virtual orbitals.
   | **Default:** 0 
   | **Datatype:** integer
   | **Recommendation:** Use default.

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
|  Fully internally contracted (Rel)MRCI            | T\. Shiozaki and W. Mizukami, J. Chem. Theory Comput. **11**, 4733 (2015)            |
+---------------------------------------------------+--------------------------------------------------------------------------------------+

