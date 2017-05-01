.. _dhf:

*************
Dirac--Hartree--Fock
*************

Description
===========

The Dirac--Hartree--Fock method performs a self-consistent field orbital optimization and energy calculation
with a four-component relativistic framework.  The Dirac--Coulomb, Dirac--Coulomb--Gaunt, or full Dirac--Coulomb--Breit 
Hamiltonian can be used.  In the BAGEL implementation, density fitting is used for the two-electron integrals, and 
2-spinor basis functions are generated using restricted kinetic balance (RKB).  
External magnetic fields can be applied, in which case the spinor basis functions are generated using restricted magnetic balance (RMB) instead.  

Dirac--Hartree--Fock (DHF) cannot be run with an odd number of electrons in the absence of an external magnetic field, due 
to the presence of multiple degenerate solutions.  For open-shell molecules, it is recommended to run relativistic 
complete active space self-consistent field (ZCASSCF) instead, possibly with a minimal active space.  
DHF can be used to generate guess orbitals by increasing the molecular charge to remove unpaired electrons.  

Command: ``dhf``

Prerequisite
=============
None

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
| General text on relativistic electronic       | Marcus Reiher and A. Wolf, Relativistic Quantum Chemistry,            |
| structure, including Dirac--Hartree--Fock.    | Wiley-VCH, Weinheim, 2009.                                            |
+-----------------------------------------------+-----------------------------------------------------------------------+
| Original implementation of density fitted     | Matthew S. Kelley and Toru Shiozaki J. Chem. Phys. 2013, 138, 204113. |
| Dirac--Hartree--Fock with RMB spinor basis.   |                                                                       |
+-----------------------------------------------+-----------------------------------------------------------------------+
| Extension to permit external magnetic fields, | Ryan D. Reynolds and Toru Shiozaki Phys. Chem. Chem. Phys. 2015, 17,  |
| including GIAO-RMB atomic basis.              | 14280-14283.                                                          |
+-----------------------------------------------+-----------------------------------------------------------------------+

