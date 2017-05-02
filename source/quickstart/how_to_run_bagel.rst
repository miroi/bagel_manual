.. _how_to_run_bagel:

*****************
How to run BAGEL
*****************

=======
Command
=======

BAGEL runs by

``BAGEL input.json``

BAGEL sends output to the standard I/O stream, so you have to pipe the output in order to save it as a file:

``BAGEL input.json > output.out``

=======================
Test input and output
=======================

This is an example input file for checking BAGEL installation.

.. code-block:: javascript 

	{ "bagel" : [

	{
		"title" : "molecule",
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

This is an example output file for checking BAGEL installation.

.. code-block:: javascript
 
  ===============================================================
    BAGEL - Freshly leavened quantum chemistry                   
  ===============================================================

  *** Geometry ***

  Symmetry: c1

  { "atom" : "F", "xyz" : [     -0.000000,     -0.000000,      2.720616 ] },
  { "atom" : "H", "xyz" : [     -0.000000,     -0.000000,      0.305956 ] },


  Number of basis functions:       19
  Number of electrons      :       10


    * METHOD: MOLECULE                             0.04

       - Overlap matrix                            0.01
       - Hcore matrix                              0.01
       - Overlap orthog                            0.00
       - Schwarz matrix                            0.00

  *** RHF ***

  === Nuclear Repulsion ===
  
     3.7272328195

      * DIIS with orbital gradients will be used.

       - SCF startup                               0.00

  === RHF iteration (svp) ===
  
               o Fock build                                  0.03
      0        -93.73328147          0.24317774           0.04
               o DIIS                                        0.00
               o Diag                                        0.00
               o Post process                                0.00
               o Fock build                                  0.03
      1        -94.07182744          0.28718754           0.04
               o DIIS                                        0.00
               o Diag                                        0.00
               o Post process                                0.00
               o Fock build                                  0.03
      2        -99.79661563          0.04248713           0.03
               o DIIS                                        0.00
               o Diag                                        0.00
               o Post process                                0.00
               o Fock build                                  0.03
      3        -99.83163247          0.02198647           0.03
               o DIIS                                        0.00
               o Diag                                        0.00
               o Post process                                0.00
               o Fock build                                  0.03
      4        -99.84455018          0.00928557           0.03
               o DIIS                                        0.00
               o Diag                                        0.00
               o Post process                                0.00
               o Fock build                                  0.03
      5        -99.84773600          0.00101157           0.03
               o DIIS                                        0.00
               o Diag                                        0.00
               o Post process                                0.00
               o Fock build                                  0.03
      6        -99.84778489          0.00026480           0.03
               o DIIS                                        0.00
               o Diag                                        0.00
               o Post process                                0.00
               o Fock build                                  0.03
      7        -99.84779021          0.00003506           0.03
               o DIIS                                        0.00
               o Diag                                        0.00
               o Post process                                0.00
               o Fock build                                  0.03
      8        -99.84779026          0.00000285           0.03
               o DIIS                                        0.00
               o Diag                                        0.00
               o Post process                                0.00
               o Fock build                                  0.03
      9        -99.84779026          0.00000042           0.03
               o DIIS                                        0.00
               o Diag                                        0.00
               o Post process                                0.00
               o Fock build                                  0.03
     10        -99.84779026          0.00000004           0.03
               o DIIS                                        0.00
               o Diag                                        0.00
               o Post process                                0.00
               o Fock build                                  0.03
     11        -99.84779026          0.00000001           0.03
               o DIIS                                        0.00
               o Diag                                        0.00
               o Post process                                0.00
               o Fock build                                  0.03
     12        -99.84779026          0.00000000           0.03
               o DIIS                                        0.00
               o Diag                                        0.00
               o Post process                                0.00
               o Fock build                                  0.03
     13        -99.84779026          0.00000000           0.03
               o DIIS                                        0.00
               o Diag                                        0.00
               o Post process                                0.00
               o Fock build                                  0.03
     14        -99.84779026          0.00000000           0.03
  
    * SCF iteration converged.

    * Permanent dipole moment:
           (    0.000000,    -0.000000,     1.055539) a.u.


    * METHOD: HF                                   0.56


  
  ===============================================================

---------------
Common mistakes
---------------
