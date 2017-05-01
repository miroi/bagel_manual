.. _hf:

*************
Hartree--Fock
*************

Description
===========
Full CI diagonalizes Full CI Hamiltonian.

.. math::
  H\Psi = E\Psi

<<<<<<< HEAD:source/scf/rhf.rst
=======
Command: ``rhf`` or ``hf``

>>>>>>> 0f1518e03e41cc8de2ab6509d0fda76d83fdd67f:source/scf/hf.rst
Prerequisite
=============
None

Keywords
========
.. topic:: ``gradient``

   | Description: to compute gradient
   | Default: false.
   | Datatype: bool
   | Values:
   |    ``TRUE`` or ``FALSE``
   | Recommendation: use default.

.. topic:: ``restart``

   | Description: to restart the calculation from an archive file
   | Default: false.
   | Datatype: bool
   | Values:
   |    ``TRUE`` or ``FALSE``
   | Recommendation: use default.

.. topic:: ``maxiter``

   | Description: to restart the calculation from 
   | Default: false.
   | Datatype: bool
   | Values:
   |    ``TRUE`` or ``FALSE``
   | Recommendation: use default.

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

