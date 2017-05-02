.. _multi:

****************************************************
Complete active space self-consistent field (CASSCF)
****************************************************

Description
===========

CASSCF simultaneously optimizes the orbital coefficients and the CI coefficients of all the possible determinants generated from the active space.
The second-order algorithm is implemented in BAGEL. The state-averaging scheme for calculating excited states is also implemented.

This algorithm is constructed by macroiterations and microiterations. At each macroiteration,
the CI coefficient is optimized by FCI calculations, while the orbitals are rotated in microiterations. 

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

   | **Description:** Specify active orbitals.
   | **Default:** Nact / 2 orbitals lower and higher from the valence orbital.
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

.. topic:: ``sort_by_coeff``

   | **Description:** Sort orbitals by coefficients or by occupation number.
   | **Default:** false.
   | **Datatype:** bool
   | **Values:**
   |    ``true``: Sort by coefficients.
   |    ``false``: Sort by occupation numbers.
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

+-----------------------------------------------+------------------------------------------------------------------------------------------------+
|          Description of Reference             |                          Reference                                                             | 
+===============================================+================================================================================================+
| Second-order orbital optimization             | T\. Yanai, Y. Kurashige, D. Ghosh, and G. K.-L. Chan, Int. J. Quantum Chem. 109, 2178 (2009).  |
+-----------------------------------------------+------------------------------------------------------------------------------------------------+

