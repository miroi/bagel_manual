.. _gradient:

****************************************
Nuclear Gradient and Derivative Coupling
****************************************

Description
===========
The force section can be used to compute the analytical gradient (force), the numerical gradient (see section on finited difference for more information), and the non-adiabatic coutpling matrix elements (NACME) 

Keywords
========

Required Keywords
-----------------
.. topic:: ``force``

   | **Description:** Requests that the gradient (force) is calculated. 

.. topic:: ``title``

   | **Description:** The title of the type of gradient calculation being performed. 
   | **Default:** N/A 
   | **Datatype:** string 
   | **Values:** (force, nacme, dgrad)
   |    ``force``: Calculates the gradient (force)
   |    ``nacme``: Calculates the non-adiabatic coupling matrix elements
   |    ``dgrad``: Difference gradient (only available for CASSCF)
   | **Recommendation:** N/A

.. topic:: ``method``

   | **Description:** The method to be used for energy evaluation 
   | **Default:** N/A 
   | **Datatype:** string 
   | **Values:**
   |    ``UHF``: Unrestricted Hartree Fock 
   |    ``ROHF``: Restricted Open-shell Hartree Fock
   |    ``HF``: Restricted Hartree Fock
   |    ``DHF`` : Dirac Hartree Fock
   |    ``MP2`` : Moller Plesset Perturbation Theory
   |    ``CASSCF`` : Complete Active Space Self Consistent Field (CASSCF)
   |    ``CASPT2`` : Complete Active Space SCF with Secont Order Perturbation Theory (CASPT2) 
   | **Recommendation:** N/A

.. topic:: ``nacmtype``

   | **Description:** Type of non-adiabatic coupling matrix element to be used.
   | **Default:** 0.
   | **Datatype:** integer
   | **Values:** 
   |    ``0``: use full nonadiabatic coupling.
   |    ``1``: use interstate coupling.
   |    ``2``: use nonadiabatic coupling with built-in electronic translational factor (ETF).
   | **Recommendation:** use default.

Optional Keywords
-----------------

.. topic:: ``numerical``

   | **Description:** The gradients will be computed using finite difference 
   | **Default:** false
   | **Datatype:** bool
   | **Values:** 
   |    ``true``: Uses finite difference
   |    ``false`` : Uses analytical gradient  
   | **Recommendation:** N/A 

.. topic:: ``diffsize``

   | **Description:** The diffsize is the step size used in the displacements in the finite difference calculations. The units are bohr. 
   | **Default:** 1.0e-3
   | **Datatype:** double precision 
   | **Recommendation:** Use default 

.. topic:: ``target``

   | **Description:** The target state for the energy and gradient evaluation (e.g. which state in a state-averaged CASSCF calculation)
   | **Default:** 0 
   | **Datatype:** integer
   | **Values:** 
   |    ``integer``: ground state = 0 
   | **Recommendation:** N/A 

.. topic:: ``target2``

   | **Description:** In an NACME or DGRAD calculation, target2 designates the target state for the second state. 
   | **Default:** 1 
   | **Datatype:** integer
   | **Values:** 
   |    ``integer``: first exited state = 1 
   | **Recommendation:** N/A 

.. topic:: ``export``

   | **Description:** 
   | **Default:** false
   | **Datatype:** bool
   | **Values:** 
   |    ````: 
   | **Recommendation:** 

.. topic:: ``export_single``

   | **Description:** 
   | **Default:** false 
   | **Datatype:** bool
   | **Values:** 
   |    ````: 
   | **Recommendation:** 

.. topic:: ``maxziter``

   | **Description:** 
   | **Default:** 100 
   | **Datatype:** int
   | **Values:** 
   |    ````: 
   | **Recommendation:** 

.. topic:: ``save_ref``

   | **Description:** 
   | **Default:** 
   | **Datatype:** 
   | **Values:** 
   |    ````: 
   | **Recommendation:** 

.. topic:: ``ref_out``

   | **Description:** 
   | **Default:** 
   | **Datatype:** 
   | **Values:** 
   |    ````: 
   | **Recommendation:** 

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
+-----------------------------------------------+-----------------------------------------------------------------------+
|          Description of Reference             |                          Reference                                    | 
+===============================================+=======================================================================+
| SS-CASPT2 gradient                            | John Doe and Jane Doe. J. Chem. Phys. 1980, 5, 120-124.               |
+-----------------------------------------------+-----------------------------------------------------------------------+
| (X)MS-CASPT2 gradient                         | John Doe and Jane Doe. J. Chem. Phys. 1980, 5, 120-124.               |
+-----------------------------------------------+-----------------------------------------------------------------------+
| (X)MS-CASPT2 derivative coupling              | John Doe and Jane Doe. J. Chem. Phys. 1980, 5, 120-124.               |
+-----------------------------------------------+-----------------------------------------------------------------------+

General References
------------------

+-----------------------------------------------+-----------------------------------------------------------------------+
|          Description of Reference             |                          Reference                                    | 
+===============================================+=======================================================================+
| Reference was used for...                     | John Doe and Jane Doe. J. Chem. Phys. 1980, 5, 120-124.               |
+-----------------------------------------------+-----------------------------------------------------------------------+
| Reference was used for...                     | John Doe and Jane Doe. J. Chem. Phys. 1980, 5, 120-124.               |
+-----------------------------------------------+-----------------------------------------------------------------------+

