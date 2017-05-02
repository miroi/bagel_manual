.. _caspt2:

********************************************************
Multireference second-order perturbation theory (CASPT2)
********************************************************


Description
===========
CASPT2 is the second-order perturbation theory based on the multiconfiguration self-consistent field theory.
Fully internally contracted single-state version (SS-CASPT2), multi-state version (MS-CASPT2) and its extended variant (XMS-CASPT2) are available.
CASPT2 in BAGEL is implemented with the automatic code generator SMITH3,
and the SMITH information for XMS-CASPT2 should be passed in a separate array in the input.

Keywords
========
CASSCF keywords
---------------
See CASSCF.

SMITH keywords
--------------

.. topic:: ``ms``

   | **Description:** Do multistate CASPT2.
   | **Default:** true.
   | **Datatype:** bool
   | **Values:**
   |    ``true``: do multistate CASPT2.
   |    ``false``: do single-state CASPT2.

.. topic:: ``xms``

   | **Description:** Do extended multistate CASPT2.
   | **Default:** true.
   | **Datatype:** bool
   | **Values:**
   |    ``true``: do XMS-CASPT2.
   |    ``false``: do MS-CASPT2.
   | **Recommendation:** use default.

.. topic:: ``sssr``

   | **Description:** Use SS-SR contraction scheme.
   | **Default:** true.
   | **Datatype:** bool
   | **Values:**
   |    ``true``: use SS-SR contraction scheme.
   |    ``false``: use MS-MR contraction scheme.
   | **Recommendation:** use default for computational efficiency

.. topic:: ``shift``

   | **Description:** Vertical shift.
   | **Default:** 0.0
   | **Datatype:** double precision
   | **Recommendation:** Increase the value if the convergence problem presents.

.. topic:: ``thresh``

   | **Description:** Convergence threshold.
   | **Default:** For single point energy calculation, 1.0e-6. Tight convergence for gradient calculation, 1.0e-8.
   | **Datatype:** double precision
   | **Recommendation:** use default.

.. topic:: ``thresh_overlap``

   | **Description:** Overlap cutoff threshold for internally contracted basis.
   | **Default:** 1.0-9
   | **Datatype:** double precision
   | **Recommendation:** use default.

.. topic:: ``frozen``

   | **Description:** Have frozen orbitals or not.
   | **Default:** true.
   | **Datatype:** bool
   | **Values:**
   |    ``true``: use frozen orbitals.
   |    ``false``: perform CASPT2 without frozen orbitals.
   | **Recommendation:** use default.

.. topic:: ``maxiter``

   | **Description:** Maximum number of iterations in CASPT2 calculations.
   | **Default:** 50
   | **Datatype:** integer
   | **Recommendation:** use default.

.. topic:: ``maxtile``

   | **Description:** Maximum number of orbitals in a single data tile used in CASPT2.
   | **Default:** 10
   | **Datatype:** integer
   | **Recommendation:** use default.

.. topic:: ``cimaxtile``

   | **Description:** Maximum number of Slater determinants in a single data tile used in CASPT2 gradient.
   | **Default:** 100 (When number of determinants is over 10000), 10 (otherwise)
   | **Datatype:** integer
   | **Recommendation:** use default. Increase further when the number of determinants is larger.


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

BAGEL References
----------------
+---------------------------------------------------+------------------------------------------------------------------------------------------+
|          Description of Reference                 |                          Reference                                                       | 
+===================================================+==========================================================================================+
| XMS-CASPT2                                        | T\. Shiozaki, W. Győrffy, P. Celani, and H.-J. Werner, J. Chem. Phys. 135, 081106 (2011).|
+---------------------------------------------------+------------------------------------------------------------------------------------------+
| SMITH3                                            | M\. K. MacLeod, and T. Shiozaki, J. Chem. Phys. 142, 010507 (2015).                      |
+---------------------------------------------------+------------------------------------------------------------------------------------------+

General References
------------------
+---------------------------------------------------+----------------------------------------------------------------------------------------------------+
|          Description of Reference                 |                          Reference                                                                 | 
+===================================================+====================================================================================================+
| CASPT2                                            | K\. Andersson, P.-Å. Malmqvist, and B. O. Roos, J. Chem. Phys. 96, 1218 (1992).                    |
+---------------------------------------------------+----------------------------------------------------------------------------------------------------+
| MS-CASPT2                                         | J\. Finley, P.-Å. Malmqvist, B. O. Roos, and L. Serrano-Andres, Chem. Phys. Lett. 288, 299 (1998). |
+---------------------------------------------------+----------------------------------------------------------------------------------------------------+
| Extended multiconfigurational perturbation theory | A\. A. Granovsky, J. Chem. Phys. 134, 214113 (2011).                                               |
+---------------------------------------------------+----------------------------------------------------------------------------------------------------+
