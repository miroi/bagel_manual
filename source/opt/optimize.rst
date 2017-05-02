.. _optimize:

*******************************
Molecular geometry optimization
*******************************

Description
===========
Three types of the geometry can be optimized: the most stable (minimum energy) geometry, conical intersections between the electronic states, and
the transition state geometry (or the saddle point on the potential energy surface). 

In the optimizations, rather than using the exact Hessian, one can
start using the approximate Hessian and update it according to the step taken.
The advanced quasi-newton optimization methods, eigenvector following (EF) algorithm and rational functional optimization (RFO) are implemented. 
In the conical intersection optimization, the
molecular gradient is replaced by the sum of the energy difference gradient and the upper state gradient after projecting the 
degeneracy lifting vectors out (gradient projection). 
In addition, the minimum energy path to the reactants and products
from the saddle point can be calculated using the second order algorithm, without mass weighting.

The output contains the gradient evaluation progress at the first step of the optimization, and the status of the optimization.
The other information, including the quantum chemistry calculations at the optimization steps, are deposited in the file ``opt.log``.

Keywords
========
Required Keywords
-----------------
.. topic:: ``optimize``

   | **Description:** Requests the geometry optimization. 

.. topic:: ``opttype``

   | **Description:** Type of the optimization calculations.
   | **Default:** energy.
   | **Datatype:** string
   | **Values:** 
   |    ``energy``: find the most stable geometry.
   |    ``conical``: find the conical intersections, according to gradient projection method.
   |    ``transition``: find the transition state geometry (saddle point on the PES).
   |    ``mep``: find the minimum energy path using the second-order algorithm, starting from the transition state geometry.

.. topic:: ``target``

   | **Description:** The target state to optimize.
   | **Default:** 0
   | **Datatype:** integer
   | **Values:**
   |    ``0``: the ground state.
   |    ``1``: the first excited state, and so on.

.. topic:: ``target2``

   | **Description:** The second target state to optimize in the conical intersection optimization.
   | **Default:** 1
   | **Datatype:** integer
   | **Values:**
   |    ``0``: the ground state.
   |    ``1``: the first excited state, and so on.

.. topic:: ``method``
   | **Description:** The method array allows the user to specify one or more methods to be used in the Hessian calculation. See section on input structure for more information. 

Convergence Criteria
--------------------

.. topic:: ``maxgrad``

   | **Description:** Maximum component of the gradient in Hartree / Bohr.
   | **Default:** 0.00001 (atoms in the molecule < 4); 0.0003 (larger).
   | **Datatype:** double precision.
   | **Recommendation:** use default.

.. topic:: ``maxdisp``

   | **Description:** Maximum component of the displacement in Bohr.
   | **Default:** 0.00004 (atoms in the molecule < 4); 0.0012 (larger).
   | **Datatype:** double precision.
   | **Recommendation:** use default.

.. topic:: ``maxchange``

   | **Description:** The energy change in Hartree.
   | **Default:** 0.000001.
   | **Datatype:** double precision.
   | **Recommendation:** use default.

Optional Keywords (Universal)
-----------------------------

.. topic:: ``algorithm``

   | **Description:** Algorithm for the optimization calculations.
   | **Default:** ef.
   | **Datatype:** string
   | **Values:** 
   |    ``ef``: Eigenvector-following (EF) algorithm.
   |    ``rfo``: Rational functional optimization algorithm.
   |    ``nr``: Newton--Raphson algorithm.
   | **Recommendation:** use either "ef" or "rfo".

.. topic:: ``maxstep``

   | **Description:** Maximum step. The unit is in the specifed coordinate.
   | **Default:** 0.3 (energy optimization); 0.1 (otherwise).
   | **Datatype:** double precision.
   | **Recommendation:** use default.

.. topic:: ``internal``

   | **Description:** Use internal coordinate or not.
   | **Default:** true.
   | **Datatype:** bool
   | **Values:**
   |    ``true``: use internal coordinates.
   |    ``false``: use Cartesian coordinates.
   | **Recommendation:** use default when you have a single molecule. If bond-breaking process is in consideration, use "false".

.. topic:: ``redundant``

   | **Description:** Use redunant internal coordinate or delocalized internal coordinate.
   | **Default:** false.
   | **Datatype:** bool
   | **Values:** 
   |    ``true``: use redundant internal coordinate.
   |    ``false``: use delocalized internal coordinate.
   | **Recommendation:** use default, except for the cases that has a problem in constructing delocalized internals (such as formaldehyde).

.. topic:: ``maxiter``

   | **Description:** Maximum number of iteration for optimization.
   | **Default:** 100.
   | **Datatype:** integer
   | **Recommendation:** use default.

.. topic:: ``maxziter``

   | **Description:** Maximum number of Z-vector iterations for gradient evaluation. Applies to SA-CASSCF, CASPT2, and MP2 calculations.
   | **Default:** 100.
   | **Datatype:** integer
   | **Recommendation:** increase the value when the Z-vector equation does not converge.

.. topic:: ``numerical``

   | **Description:** Use numerical gradient.
   | **Default:** false.
   | **Datatype:** bool
   | **Values:** 
   |    ``true``: use numerical gradient.
   |    ``false``: use analytical gradient.
   | **Recommendation:** use default.

.. topic:: ``numerical_dx``

   | **Description:** \Delta x for numerical gradient.
   | **Default:** 0.001 (bohr).
   | **Datatype:** double precision
   | **Recommendation:** use default.

.. topic:: ``hess_update``

   | **Description:** Hessian updating scheme.
   | **Default:** flowchart.
   | **Datatype:** string
   | **Values:** 
   |    ``flowchart``: use flowchart update. This automatically decides according to the shape of PES.
   |    ``bfgs``: use BFGS scheme.
   |    ``psb``: use PSB scheme.
   |    ``sr1``: use SR1 scheme.
   | **Recommendation:** use default.

.. topic:: ``hess_approx``

   | **Description:** Use approximate Hessian for the initial step of the optimization.
   | **Default:** true.
   | **Datatype:** bool
   | **Values:** 
   |    ``true``: use approximate Hessian.
   |    ``false``: calculate numerical Hessian first, and start the optimization using the Hessian.
   | **Recommendation:** use default.

.. topic:: ``adaptive``

   | **Description:** Use adaptive stepsize in RFO algorithm.
   | **Default:** true (algorithm is RFO); false (otherwise).
   | **Datatype:** bool
   | **Values:** 
   |    ``true``: use adaptive maximum stepsize.
   |    ``false``: use fixed maximum stepsize.
   | **Recommendation:** use default.

Optional Keywords (Conical Intersection Optimization)
-----------------------------------------------------

.. topic:: ``nacmtype``

   | **Description:** Type of non-adiabatic coupling matrix element to be used.
   | **Default:** 1.
   | **Datatype:** integer
   | **Values:** 
   |    ``0``: use full nonadiabatic coupling.
   |    ``1``: use interstate coupling.
   |    ``2``: use nonadiabatic coupling with built-in electronic translational factor (ETF).
   | **Recommendation:** use default.

.. topic:: ``thielc3``

   | **Description:** Thiel's C_3 parameter, which is multiplied to the full gradient. 
   | **Default:** 2.0.
   | **Datatype:** double precision
   | **Recommendation:** use default.

.. topic:: ``thielc4``

   | **Description:** Thiel's C_4 parameter, which is multiplied to the gradient difference.
   | **Default:** 0.5
   | **Datatype:** double precision
   | **Recommendation:** use default.

Optional Keywords (Minimum Energy Path)
---------------------------------------

.. topic:: ``mep_direction``

   | **Description:** Direction of the MEP calculation from the transition state.
   | **Default:** 1.
   | **Datatype:** integer
   | **Values:** 
   |    ``1``: use the direction of the lowest eigenvector.
   |    ``-1``: use the opposite direction of the lowest eigenvector.
   | **Recommendation:** run two calculations with "1" and "-1" to get the full path.


Example
=======
This optimizes the ground state geometry of hydrogen fluoride in the ground state, using two-state averaged CAASCF with active space of (2e,2o).

Sample input
------------

.. code-block:: javascript 

   { "bagel" : [

   {
     "title" : "molecule",
     "basis" : "svp",
     "df_basis" : "svp-jkfit",
     "angstrom" : false,
     "geometry" : [
       { "atom" : "H",  "xyz" : [   -0.000000,     -0.000000,      1.700000] },
       { "atom" : "F",  "xyz" : [   -0.000000,     -0.000000,      0.000000] }
     ]
   },

   {
     "title" : "optimize",
     "method" : [ {
       "title" : "casscf",
       "nact" : 0,
       "nact_cas" : 2,
       "nclosed" : 4,
       "nstate" : 2
     } ]
   }

   ]}

This optimization ends in three steps.


References
==========

+-----------------------------------------------+--------------------------------------------------------------------------------------+
|          Description of Reference             |                          Reference                                                   | 
+===============================================+======================================================================================+
| Eigenvector following algorithm               | J\. Baker, J. Comput. Chem. 7, 385 (1986).                                           |
+-----------------------------------------------+--------------------------------------------------------------------------------------+
| Rational functional optimization algorithm    | A\. Banerjee, N. Adams, J. Simons, and R. J. Shepard, J. Phys. Chem. 89, 52 (1985).  |
+-----------------------------------------------+--------------------------------------------------------------------------------------+
| Second-order minimum energy path search       | C\. Gonzalez and H. B. Schlegel, J. Chem. Phys. 90, 2154 (1989).                     |
+-----------------------------------------------+--------------------------------------------------------------------------------------+
| Gradient projection algorithm                 | M\. J. Bearpark, M. A. Robb, and H. B. Schlegel, Chem. Phys. Lett. 223, 269 (1994).  |
+-----------------------------------------------+--------------------------------------------------------------------------------------+
| Flowchart method                              | A\. B. Birkholz, and H. B. Schlegel, Theor. Chem. Acc. 135, 84 (2016).               |
+-----------------------------------------------+--------------------------------------------------------------------------------------+
| ETF in nonadiabatic coupling                  | S\. Fatehi, and J. E. Subotnik, J. Phys. Chem. Lett. 3, 2039 (2012).                 |
+-----------------------------------------------+--------------------------------------------------------------------------------------+
| Thiel's conical intersection parameters       | T\. W. Keal, A. Koslowski and W. Thiel, Theor. Chem. Acc. 118, 837 (2007).           |
+-----------------------------------------------+--------------------------------------------------------------------------------------+

