.. _grad_hesse:

*******
Hessian
*******

Description
===========
The Hessian section can be used to compute the numerical Hessian by central gradient differences. The Hessian, mass weighted Hessian, and symmetrized mass weighted Hessian are printed in the output by default. The rotational and translational degrees of freedom have been projected out. Vibrational frequencies, infrared intensities, and the cartesian eigenvectors of each normal mode are also computed. The masses are averaged over the natural occurance of isotopes. 

Required Keywords
=================
.. topic:: ``hessian``

   | **Description:** Requests that the Numerical hessian be computed 

.. topic:: ``method``

   | **Description:** The method to be used for the gradient calculations for each displacment when computing the numerical Hessian by central gradient differences 
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

.. topic:: ``dx``

   | **Description:** The step size used in the displacements in the gradient difference calculations. The units are bohr. 
   | **Default:** 1.0e-3
   | **Datatype:** double precision 
   | **Recommendation:** Use default 

Optional Keywords
=================

.. topic:: ``nproc``

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

+-----------------------------------------------+-----------------------------------------------------------------------+
|          Description of Reference             |                          Reference                                    | 
+===============================================+=======================================================================+
| Vibrational Specroscopy book                  | John Doe and Jane Doe. J. Chem. Phys. 1980, 5, 120-124.               |
+-----------------------------------------------+-----------------------------------------------------------------------+
| Reference was used for...                     | John Doe and Jane Doe. J. Chem. Phys. 1980, 5, 120-124.               |
+-----------------------------------------------+-----------------------------------------------------------------------+

