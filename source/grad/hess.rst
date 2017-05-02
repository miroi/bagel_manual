.. _grad_hesse:

****************************************
Molecular hessian and frequency analysis
****************************************

Description
===========
The Hessian section can be used to compute the numerical Hessian by central gradient differences. The Hessian, mass weighted Hessian, and symmetrized mass weighted Hessian are printed in the output by default. The rotational and translational degrees of freedom have been projected out. Vibrational frequencies, infrared intensities, and the cartesian eigenvectors of each normal mode are also computed. The masses are averaged over the natural occurance of isotopes. 

Required Keywords
=================
.. topic:: ``hessian``

   | **Description:** Requests that the Numerical hessian be computed 

.. topic:: ``method``

   | **Description:** The method to be used for the analytical gradient calculation (or for the energy evaluation when compyting the gradient by finite difference. 
   | **Default:** N/A 
   | **Datatype:** string 
   | **Values:**
   |    ``UHF``: Unrestricted Hartree–Fock 
   |    ``ROHF``: Restricted Open-shell Hartree–Fock
   |    ``HF``: Restricted Hartree–Fock
   |    ``DHF`` : Dirac–Hartree–Fock
   |    ``MP2`` : Moller–Plesset perturbation theory
   |    ``CASSCF`` : Complete active space self consistent field (CASSCF)
   |    ``CASPT2`` : Multireference perturbation theory (CASPT2) 
   | **Recommendation:** N/A

.. topic:: ``dx``

   | **Description:** The step size used in the displacements in the gradient difference calculations. The units are bohr. 
   | **Default:** 1.0e-3
   | **Datatype:** double precision 
   | **Recommendation:** Use default 

Optional Keywords
=================

.. topic:: ``nproc``

   | **Description:** The Hessian code is parallelized so that the displacements in the central gradient difference calculations can be run at the same time. The nproc keyword allows the user to specify the number of MPI processes to be used for each gradient calculation. 
   | **Default:** 1
   | **Datatype:** integer
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

References
==========

+----------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------+
|          Description of Reference                  |                          Reference                                                                                    | 
+====================================================+=======================================================================================================================+
| General description of vibrational spectroscopy    | E. Bright Wilson, Jr., J.C. Decius, and Paul C. Cross. Molecular Vibrations. Dover Publications, Inc. New York, 1955. |
+----------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------+

