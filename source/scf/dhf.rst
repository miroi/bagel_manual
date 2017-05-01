.. _hf:

*************
Hartree--Fock
*************

Description
===========



Command: ``dhf``

Prerequisite
=============


Keywords
========
.. topic:: ``gaunt``

   | Description:
   | Default: false.
   | Datatype: bool
   | Recommendation:

.. topic:: ``breit``

   | Description:
   | Default: false.
   | Datatype: bool
   | Recommendation:

.. topic:: ``robust``

   | Description:
   | Default: false.
   | Datatype: bool
   | Recommendation:

.. topic:: ``gradient``

   | Description:
   | Default: false.
   | Datatype: bool
   | Recommendation:

.. topic:: ``maxiter (overwrites maxiter_scf)``

   | Description:
   | Default: 100
   | Datatype: int
   | Recommendation:

.. topic:: ``diis_start``

   | Description:
   | Default: 1
   | Datatype: int
   | Values:
   |
   | Recommendation:

.. topic:: ``thresh (overwrites thresh_scf)``

   | Description:
   | Default: 1.0e-8
   | Datatype: double
   | Values:
   |
   | Recommendation:

.. topic:: ``thresh_overlap``

   | Description:
   | Default: 1.0e-8
   | Datatype: double
   | Values:
   |
   | Recommendation:

.. topic:: ``charge``

   | Description:
   | Default: 0
   | Datatype: int
   | Values:
   |
   | Recommendation:

.. topic:: ``multipole``

   | Description:
   | Default: 1
   | Datatype: int
   | Values:
   |
   | Recommendation:

.. topic:: ``pop``

   | Description:
   | Default: false
   | Datatype: bool
   | Recommendation:


Example
=======
This should be an example that is chemically relevant. There should be text explaining what the example is and why it's interesting.

Sample input
------------

.. code-block:: javascript 

	{ "bagel" : [

	{
	  "title" : "molecule",
		"symmetry" : "C1",
		"basis" : "svp",
		"df_basis" : "svp-jkfit",
		"angstrom" : "false",
		"geometry" : [
			{ "atom" : "F",  "xyz" : [ -0.000000,     -0.000000,      2.720616]},
			{ "atom" : "H",  "xyz" : [ -0.000000,     -0.000000,      0.305956]}
		]
	},

	{
		"title" : "hf",
		"thresh" : 1.0e-10
	},

	{
		"title" : "dhf",
		"gaunt" : true,
		"breit" : true
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

