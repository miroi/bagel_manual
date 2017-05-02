.. _force:

*****
Force
*****

Description
===========
The force section can be used to compute the analytical gradient (force), the numerical gradient by finite difference, or the non-adiabatic coupling matrix elements (NACME). Analytical gradients are implemented for unrestricted Hartree Fock (UHF), restricted open-shell Hartree Fock (ROHF), restricted Hartree Fock (RHF), Dirac Hartree Fock (DHF), Moller Plesset Perturbation Theory (MP2), complete active space self consistent field (CASSCF), and CASSCF with second order perturbation theory (CASPT2). 

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

   | **Description:** The method to be used for the analytical gradient calculation (or for the energy evaluation when compyting the gradient by finite difference. 
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

   | **Description:** Type of non-adiabatic coupling matrix element to be used
   | **Default:** 0
   | **Datatype:** integer
   | **Values:** 
   |    ``0``: Use full non-adiabatic coupling
   |    ``1``: Use interstate coupling 
   |    ``2``: Use non-adiabtic coupling with built-in electronic translational factor (ETF)
   | **Recommendation:** use default 

Optional Keywords
-----------------

.. topic:: ``numerical``

   | **Description:** The gradients will be computed by finite difference. 
   | **Default:** false
   | **Datatype:** bool
   | **Values:** 
   |    ``true``: Uses finite difference
   |    ``false`` : Uses analytical gradient  
   | **Recommendation:** If available, use analytical gradient. 

.. topic:: ``dx``

   | **Description:** The step size used in the displacements in the finite difference calculations. The units are bohr. 
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

   | **Description:** This option will export the nuclear gradient to a text file.  
   | **Default:** false
   | **Datatype:** bool
   | **Values:** 
   |    ``true``: Export file
   |    ``false``: Do not export file 
   | **Recommendation:** This is used to interface with the QM/MM program. See section on non-adiabatic dynamics. 

.. topic:: ``export_single``

   | **Description:** This option will export the nuclear gradient to a text file for a single state.  
   | **Default:** false 
   | **Datatype:** bool
   | **Values:** 
   |    ``true``: Export file
   |    ``false``: Do not export file 
   | **Recommendation:** This is used to interface with the QM/MM program. See section on non-adiabatic dynamics.

.. topic:: ``maxziter``

   | **Description:** Maximum number of Z-vector iterations for gradient evaluation. Applies to CASSCF, CASPT2, and MP2 calculations.
   | **Default:** 100 
   | **Datatype:** integer
   | **Recommendation:** Increase the value when Z-vector equation does not converge.

.. topic:: ``save_ref``

   | **Description:** The reference wavefunction is saved to an archive file. 
   | **Default:** false
   | **Datatype:** bool
   | **Values:** 
   |    ``true``: Archive file is saved 
   |    ``false`` : Archive file is not saved
   | **Recommendation:** Save file if it is likely that the calculation will need to be restarted 

.. topic:: ``ref_out``

   | **Description:** The name of the archive file for the stored reference. The path to the location the file should be written can also be specified here. 
   | **Datatype:** string

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
+-----------------------------------------------+---------------------------------------------------------------------------------+
|          Description of Reference             |                          Reference                                              | 
+===============================================+=================================================================================+
| SS-CASPT2 gradient                            |  MacLeod, M. K. and Shiozaki. T. J. Chem. Phys. 2015, 142, 051103.              |
+-----------------------------------------------+---------------------------------------------------------------------------------+
| (X)MS-CASPT2 gradient                         | Vlaisavljevich, B. and Shiozaki, T. J. Chem. Theory Comput. 2016, 12, 3781-3787.| 
+-----------------------------------------------+---------------------------------------------------------------------------------+
| (X)MS-CASPT2 derivative coupling              | Park, J. W. and Shiozaki, T. Submitted.                                         |
+-----------------------------------------------+---------------------------------------------------------------------------------+

General References
------------------

+-----------------------------------------------+--------------------------------------------------------------------------------+
|          Description of Reference             |                          Reference                                             | 
+===============================================+================================================================================+
| General review of gradient methods            | Pulay, P. WIREs Comput. Mol. Sci. 2014, 4, 169-181.                            |
+-----------------------------------------------+--------------------------------------------------------------------------------+
| Reference was used for...                     | John Doe and Jane Doe. J. Chem. Phys. 1980, 5, 120-124.                        |
+-----------------------------------------------+--------------------------------------------------------------------------------+

