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

Command: ``caspt2``

Keywords
========
CASSCF keywords
---------------
See :ref:`casscf`.

SMITH keywords
--------------

.. topic:: ``ms``

   | **Description:** Do multistate CASPT2.
   | **Default:** true.
   | **Datatype:** bool
   | **Values:**
   |    ``true``: Do multistate CASPT2.
   |    ``false``: Do single-state CASPT2.

.. topic:: ``xms``

   | **Description:** Do extended multistate CASPT2.
   | **Default:** true.
   | **Datatype:** bool
   | **Values:**
   |    ``true``: Do XMS-CASPT2.
   |    ``false``: Do MS-CASPT2.
   | **Recommendation:** Use default.

.. topic:: ``sssr``

   | **Description:** Use SS-SR contraction scheme.
   | **Default:** true.
   | **Datatype:** bool
   | **Values:**
   |    ``true``: use SS-SR contraction scheme.
   |    ``false``: use MS-MR contraction scheme.
   | **Recommendation:** Use default for computational efficiency

.. topic:: ``shift``

   | **Description:** Vertical shift.
   | **Default:** 0.0
   | **Datatype:** double precision
   | **Recommendation:** Use default. Increase the value if the convergence problem presents.

.. topic:: ``thresh``

   | **Description:** Convergence threshold.
   | **Default:** For single point energy calculation, 1.0e-6. Tight convergence for gradient calculation, 1.0e-8.
   | **Datatype:** double precision
   | **Recommendation:** Use default.

.. topic:: ``thresh_overlap``

   | **Description:** Overlap cutoff threshold for internally contracted basis.
   | **Default:** 1.0-9
   | **Datatype:** Double precision
   | **Recommendation:** Use default.

.. topic:: ``frozen``

   | **Description:** Have frozen orbitals or not.
   | **Default:** true.
   | **Datatype:** bool
   | **Values:**
   |    ``true``: Use frozen orbitals.
   |    ``false``: Perform CASPT2 without frozen orbitals.
   | **Recommendation:** Use default.

.. topic:: ``maxiter``

   | **Description:** Maximum number of iterations in CASPT2 calculations.
   | **Default:** 50
   | **Datatype:** integer
   | **Recommendation:** Use default.

.. topic:: ``maxtile``

   | **Description:** Maximum number of orbitals in a single data tile used in CASPT2.
   | **Default:** 10
   | **Datatype:** integer
   | **Recommendation:** Use default.

.. topic:: ``cimaxtile``

   | **Description:** Maximum number of Slater determinants in a single data tile used in CASPT2 gradient.
   | **Default:** 100 (When number of determinants is over 10000), 10 (otherwise)
   | **Datatype:** integer
   | **Recommendation:** Use default. Increase further when the number of determinants is larger.


Example
=======
XMS-CASPT2 calculation based on the two-state CASSCF reference function, with vertical shift of 0.2 :math:`E_h`. "SS-SR" contraction scheme is used.
The active space of (6e,6o), which comprises three :math:`\pi` and three :math:`\pi^*` orbitals, is used.

Sample input
------------

.. code-block:: javascript

  { "bagel" : [

  {
    "title" : "molecule",
    "basis" : "svp",
    "df_basis" : "svp-jkfit",
    "geometry" : [
    { "atom" : "C", "xyz" : [     -0.079002,      2.543870,      0.000000 ] },
    { "atom" : "C", "xyz" : [      2.557470,      2.543870,      0.000000 ] },
    { "atom" : "C", "xyz" : [      3.875630,      4.826190,      0.000000 ] },
    { "atom" : "C", "xyz" : [      2.557250,      7.109950,     -0.002266 ] },
    { "atom" : "C", "xyz" : [     -0.078588,      7.109800,     -0.003171 ] },
    { "atom" : "C", "xyz" : [     -1.396870,      4.826620,     -0.001289 ] },
    { "atom" : "H", "xyz" : [     -1.117900,      0.744245,      0.000850 ] },
    { "atom" : "H", "xyz" : [      3.595900,      0.743875,      0.002485 ] },
    { "atom" : "H", "xyz" : [      5.953730,      4.826340,      0.001198 ] },
    { "atom" : "H", "xyz" : [      3.596980,      8.909240,     -0.002377 ] },
    { "atom" : "H", "xyz" : [     -1.118170,      8.909350,     -0.004972 ] },
    { "atom" : "H", "xyz" : [     -3.474820,      4.826960,     -0.001629 ] }
    ]
  },
  {
    "title" : "caspt2",
    "smith" : {
      "method" : "caspt2",
      "ms" : true,
      "xms" : true,
      "sssr" : true,
      "shift" : 0.2
    }
    "nstate" : 2,
    "nact" : 6,
    "nclosed" : 18,
    "active" : [17, 20, 21, 22, 23, 30]
  }
  ]}

References
==========

BAGEL References
----------------
+---------------------------------------------------+----------------------------------------------------------------------------------------------+
|          Description of Reference                 |                          Reference                                                           | 
+===================================================+==============================================================================================+
| XMS-CASPT2                                        | T\. Shiozaki, W. Győrffy, P. Celani, and H.-J. Werner, J. Chem. Phys. **135**, 081106 (2011).|
+---------------------------------------------------+----------------------------------------------------------------------------------------------+
| SMITH3                                            | M\. K. MacLeod, and T. Shiozaki, J. Chem. Phys. **142**, 010507 (2015).                      |
+---------------------------------------------------+----------------------------------------------------------------------------------------------+

General References
------------------
+---------------------------------------------------+-------------------------------------------------------------------------------------------------------+
|          Description of Reference                 |                          Reference                                                                    | 
+===================================================+=======================================================================================================+
| CASPT2                                            | K\. Andersson, P.-Å. Malmqvist, and B. O. Roos, J. Chem. Phys. **96**, 1218 (1992).                   |
+---------------------------------------------------+-------------------------------------------------------------------------------------------------------+
| MS-CASPT2                                         | J\. Finley, P.-Å. Malmqvist, B. O. Roos, and L. Serrano-Andres, Chem. Phys. Lett. **288**, 299 (1998).|
+---------------------------------------------------+-------------------------------------------------------------------------------------------------------+
| Extended multiconfigurational perturbation theory | A\. A. Granovsky, J. Chem. Phys. **134**, 214113 (2011).                                              |
+---------------------------------------------------+-------------------------------------------------------------------------------------------------------+
