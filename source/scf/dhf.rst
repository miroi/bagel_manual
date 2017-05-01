.. _dhf:

*************
Dirac--Hartree--Fock
*************

Description
===========


Keywords
========
The default values are recommended unless mentioned otherwise.

.. topic:: ``gaunt``

   | Description:
   | Default: false
   | Datatype: bool
   | Recommendation: use default.

.. topic:: ``breit``

   | Description:
   | Default: gaunt
   | Datatype: bool
   | Recommendation: use default.

.. topic:: ``robust``

   | Description:
   | Default: false
   | Datatype: bool
   | Recommendation: use default.

.. topic:: ``gradient``

   | Description:
   | Default: false
   | Datatype: bool
   | Recommendation: use default.

.. topic:: ``maxiter (overwrites maxiter_scf)``

   | Description:
   | Default: 100
   | Datatype: int
   | Recommendation: use default.

.. topic:: ``diis_start``

   | Description:
   | Default: 1
   | Datatype: int
   | Recommendation: use default.

.. topic:: ``thresh (overwrites) thresh_scf``

   | Description:
   | Default: 1.0e-8
   | Datatype: double
   | Recommendation: use default.

.. topic:: ``thresh_overlap``

   | Description:
   | Default: 1.0e-8
   | Datatype: double
   | Recommendation: use default.

.. topic:: ``charge``

   | Description:
   | Default: 0
   | Datatype: int
   | Recommendation:

.. topic:: ``multipole``

   | Description:
   | Default: 1
   | Datatype: int
   | Recommendation:

.. topic:: ``pop``

   | Description:
   | Default: false
   | Datatype: bool
   | Recommendation:

Example
=======
This should be an example that is chemically relevant. There should be text explaining what the example is and why it's interesting.

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

References
==========

+-----------------------------------------------+-----------------------------------------------------------------------+
|          Description of Reference             |                          Reference                                    | 
+===============================================+=======================================================================+
| Reference was used for...                     | John Doe and Jane Doe. J. Chem. Phys. 1980, 5, 120-124.               |
+-----------------------------------------------+-----------------------------------------------------------------------+
| Reference was used for...                     | John Doe and Jane Doe. J. Chem. Phys. 1980, 5, 120-124.               |
+-----------------------------------------------+-----------------------------------------------------------------------+

