.. _how_to_run_bagel:

*****************
How to run BAGEL
*****************

=======
Command
=======

BAGEL runs by ::

   BAGEL input.json

BAGEL sends output to the standard I/O stream, so you have to pipe the output in order to save it as a file: ::

   BAGEL input.json > output.out

=======================
Test input and output
=======================

This is an example input file for checking the BAGEL installation.

.. code-block:: javascript

  { "bagel" : [

  {
    "title" : "molecule",
    "basis" : "svp",
    "df_basis" : "svp-jkfit",
    "angstrom" : "false",
    "geometry" : [
      { "atom" : "F",  "xyz" : [ -0.000000,     -0.000000,      2.720616]},
      { "atom" : "H",  "xyz" : [ -0.000000,     -0.000000,      0.305956]}
    ]
  },

  {
    "title" : "hf"
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

  Number of auxiliary basis functions:       95

  Since a DF basis is specified, we compute 2- and 3-index integrals:
    o Being stored without compression. Storage requirement is 0.000 GB
       - 3-index ints prep                         0.00
       - 3-index ints                              0.02
       - 2-index ints                              0.01
       - computing inverse                         0.17
        elapsed time:        0.21 sec.


  Number of basis functions:       19
  Number of electrons      :       10


    * METHOD: MOLECULE                             0.37

       - Overlap matrix                            0.01
       - Hcore matrix                              0.02
       - Overlap orthog                            0.00

  *** RHF ***

  === Nuclear Repulsion ===

     3.7272328195

      * DIIS with orbital gradients will be used.

       - SCF startup                               0.56

  === RHF iteration (svp) ===

               o Fock build                                  0.02
      0        -99.70639103          0.06595513           0.02
               o DIIS                                        0.00
               o Diag                                        0.00
               o Post process                                0.00
               o Fock build                                  0.02
      1        -99.78677680          0.04496384           0.02
               o DIIS                                        0.00
               o Diag                                        0.00
               o Post process                                0.00
               o Fock build                                  0.02
      2        -99.84655378          0.00434989           0.02
               o DIIS                                        0.00
               o Diag                                        0.00
               o Post process                                0.00
               o Fock build                                  0.02
      3        -99.84766336          0.00089762           0.02
               o DIIS                                        0.00
               o Diag                                        0.00
               o Post process                                0.00
               o Fock build                                  0.02
      4        -99.84772173          0.00015090           0.02
               o DIIS                                        0.00
               o Diag                                        0.00
               o Post process                                0.00
               o Fock build                                  0.02
      5        -99.84772349          0.00002429           0.02
               o DIIS                                        0.00
               o Diag                                        0.00
               o Post process                                0.00
               o Fock build                                  0.02
      6        -99.84772354          0.00000255           0.02
               o DIIS                                        0.00
               o Diag                                        0.00
               o Post process                                0.00
               o Fock build                                  0.02
      7        -99.84772354          0.00000043           0.02
               o DIIS                                        0.00
               o Diag                                        0.00
               o Post process                                0.00
               o Fock build                                  0.02
      8        -99.84772354          0.00000012           0.02
               o DIIS                                        0.00
               o Diag                                        0.00
               o Post process                                0.00
               o Fock build                                  0.02
      9        -99.84772354          0.00000004           0.02
               o DIIS                                        0.00
               o Diag                                        0.00
               o Post process                                0.00
               o Fock build                                  0.02
     10        -99.84772354          0.00000000           0.02
               o DIIS                                        0.00
               o Diag                                        0.00
               o Post process                                0.00
               o Fock build                                  0.02
     11        -99.84772354          0.00000000           0.02
               o DIIS                                        0.00
               o Diag                                        0.00
               o Post process                                0.00
               o Fock build                                  0.02
     12        -99.84772354          0.00000000           0.02

    * SCF iteration converged.

    * Permanent dipole moment:
           (    0.000000,    -0.000000,     1.055510) a.u.


    * METHOD: HF                                   0.83



  ===============================================================
