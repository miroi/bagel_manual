.. _dhf:

*************
Dirac--Hartree--Fock
*************

Description
===========

.. math::
  H\Psi = E\Psi

Command: ``rhf`` or ``hf``

Prerequisite
=============
None

Keywords
========
.. topic:: ``gradient``

   | Description: to compute gradient
   | Default: false
   | Datatype: bool
   | Recommendation: use default.

.. topic:: ``restart``

   | Description: to restart the calculation from an archive file
   | Default: false
   | Datatype: bool
   | Recommendation: use default.

.. topic:: ``maxiter``

   | Description: number of iterations
   | Default: 100
   | Datatype: integer 

.. topic:: ``maxiter``

   | Description: number of iterations
   | Default: 100
   | Datatype: integer 

.. topic:: ``maxiter_scf``

   | Description: number of SCF iterations, which is the same as ``maxiter`` if you are only running SCF calculations
   | Datatype: integer 
   
.. topic:: ``diis_start``
.. topic:: ``diis_size``
.. topic:: ``thresh_overlap``
.. topic:: ``thresh``
.. topic:: ``thresh_scf``
   |
  max_iter_ = idata_->get<int>("maxiter", 100);
  max_iter_ = idata_->get<int>("maxiter_scf", max_iter_);
  diis_start_ = idata_->get<int>("diis_start", 1);
  diis_size_ = idata_->get<int>("diis_size", 5);
  thresh_overlap_ = idata_->get<double>("thresh_overlap", 1.0e-8);
  thresh_scf_ = idata_->get<double>("thresh", 1.0e-8);

Example
=======
This should be an example that is chemically relevant. There should be text explaining what the example is and why it's interesting.

Sample input
------------

.. code-block:: javascript 

   { "bagel" : [
   
   {
     "title" : "molecule",
     "symmetry" : "C2v",
     "basis" : "svp",
     "angstrom" : "false",
     "geometry" : [
       { "atom" : "F",  "xyz" : [ -0.000000,     -0.000000,      2.720616]},
       { "atom" : "H",  "xyz" : [ -0.000000,     -0.000000,      0.305956]}
     ]
   },
   
   {
     "title" : "hf",
     "df" : false,
     "thresh" : 1.0e-10
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
| Reference was used for...                     | John Doe and Jane Doe. J. Chem. Phys. 1980, 5, 120-124.               |
+-----------------------------------------------+-----------------------------------------------------------------------+
| Reference was used for...                     | John Doe and Jane Doe. J. Chem. Phys. 1980, 5, 120-124.               |
+-----------------------------------------------+-----------------------------------------------------------------------+

