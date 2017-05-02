.. _force:

****************************************
Nuclear gradient and derivative coupling
****************************************

Description
===========
The force section can be used to compute the analytical gradient (force), the numerical gradient by finite difference, or the non-adiabatic coupling matrix elements (NACME). Analytical gradients are implemented for unrestricted Hartree–Fock (UHF), restricted open-shell Hartree–Fock (ROHF), restricted Hartree–Fock (RHF), Dirac–Hartree–Fock (DHF), Moller–Plesset perturbation theory (MP2), complete active space self consistent field (CASSCF), and multireference perturbation theory (CASPT2). 

Method Array
===========
The method array allows the user to specify one or more methods to be used in the force calculation. This is used, for example, to compute CASPT2 gradients where the CASSCF calculation must first be performed.  

.. code-block:: javascript 

  {
    "title" : "force",
      "method" : [ {
      "title" : "caspt2",
        "smith" : {
           "method" : "caspt2",
           "shift" : 0.2,
           "frozen" : true
      },
      "nstate" : 3,
      "nact_cas" : 7,
      "nclosed" : 44 
    } ]
  }

.. code-block:: javascript 

  {
    "title" : "force",
      "method" : [ 
        {
          "title" : "casscf",
          "nstate" : 3,
           "nact_cas" : 7,
           "nclosed" : 44
        },

        {
          "title" : "caspt2",
          "method" : "caspt2",
          "shift" : 0.2,
          "frozen" : true
        } 
      ]
  }
 
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
   | **Recommendation:** If available, use analytical gradient. If analytical gradient is not available, BAGEL automatically switches to numerical gradient.

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

   | **Description:** Maximum number of Z-vector iterations for gradient evaluation. Applies to SA-CASSCF, CASPT2, and MP2 calculations.
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
The benzophenone molecule

.. figure:: benzophenone.png
    :width: 200px
    :align: center
    :alt: alternate text
    :figclass: align-center

    The benzophenone molecule with carbon atoms in grey, oxygen in red, and hydrogen in white. 
 
Sample input: force
-------------------

.. code-block:: javascript 

  { "bagel" : [

  {
    "title" : "molecule",
    "symmetry" : "C1",
    "basis" : "cc-pvdz",
    "df_basis" : "cc-pvdz-jkfit",
    "angstrom" : false,
    "geometry" : [
    { "atom" : "C", "xyz" : [     -2.002493,     -2.027773,      0.004882 ] },
    { "atom" : "C", "xyz" : [     -2.506057,     -4.613700,      0.009896 ] },
    { "atom" : "C", "xyz" : [      0.536515,     -1.276360,      0.003515 ] },
    { "atom" : "C", "xyz" : [     -0.558724,     -6.375134,      0.013503 ] },
    { "atom" : "H", "xyz" : [     -4.396140,     -5.341490,      0.011057 ] },
    { "atom" : "C", "xyz" : [      2.478233,     -3.024614,      0.007049 ] },
    { "atom" : "H", "xyz" : [      0.959539,      0.714937,     -0.000292 ] },
    { "atom" : "C", "xyz" : [      1.936441,     -5.592475,      0.012127 ] },
    { "atom" : "H", "xyz" : [     -1.012481,     -8.367883,      0.017419 ] },
    { "atom" : "H", "xyz" : [      4.418042,     -2.380738,      0.005919 ] },
    { "atom" : "H", "xyz" : [      3.448750,     -6.968581,      0.014980 ] },
    { "atom" : "C", "xyz" : [     -6.758666,     -0.057378,      0.001157 ] },
    { "atom" : "C", "xyz" : [     -8.231109,     -2.241648,      0.000224 ] },
    { "atom" : "C", "xyz" : [     -8.022986,      2.269249,      0.001194 ] },
    { "atom" : "C", "xyz" : [    -10.853532,     -2.110536,     -0.000769 ] },
    { "atom" : "H", "xyz" : [     -7.410047,     -4.093049,      0.000224 ] },
    { "atom" : "C", "xyz" : [    -10.632155,      2.405932,      0.000369 ] },
    { "atom" : "H", "xyz" : [     -6.913797,      3.976253,      0.001805 ] },
    { "atom" : "C", "xyz" : [    -12.064741,      0.207004,     -0.000695 ] },
    { "atom" : "H", "xyz" : [    -11.941318,     -3.840822,     -0.001614 ] },
    { "atom" : "H", "xyz" : [    -11.548963,      4.232744,      0.000447 ] },
    { "atom" : "H", "xyz" : [    -14.107194,      0.302907,     -0.001460 ] },
    { "atom" : "C", "xyz" : [     -3.892311,      0.136360,      0.001267 ] },
    { "atom" : "O", "xyz" : [     -3.026383,      2.227189,     -0.001563 ] }
    ]
  },

  {
    "title" : "force",
     "method" : [ {
      "title" : "hf",
      "thresh" : 1.0e-12
    } ]
  }
 ]}


Methods that require the use of smith: 

.. code-block:: javascript 

  {
    "title" : "force",
     "target" : 0,
     "method" : [ {
       "title" : "caspt2",
         "smith" : {
           "method" : "caspt2",
           "ms" : "true",
           "xms" : "true",
           "sssr" : "true",
           "shift" : 0.2,
           "frozen" : true
       },
       "nstate" : 3,
       "nact_cas" : 7,
       "nclosed" : 44
     } ]
   }

Sample input: NACME and DGRAD 
-----------------------------

.. code-block:: javascript 

  {
    "title" : "force",
     "target" : 0,
     "method" : [ {
       "title" : "caspt2",
         "smith" : {
           "method" : "caspt2",
           "ms" : "true",
           "xms" : "true",
           "sssr" : "true",
           "shift" : 0.2,
           "frozen" : true
       },
       "nstate" : 3,
       "nact_cas" : 7,
       "nclosed" : 44 
     } ]
   }

Some information about the output should also be included. This will not be entire output but enough for the reader to know their calculation worked.


References
==========

BAGEL References
----------------
+-----------------------------------------------+---------------------------------------------------------------------------------+
|          Description of Reference             |                          Reference                                              | 
+===============================================+=================================================================================+
| SS-CASPT2 gradient                            | M\. K. MacLeod and T. Shiozaki. J. Chem. Phys. 142, 051103 (2015)               |
+-----------------------------------------------+---------------------------------------------------------------------------------+
| (X)MS-CASPT2 gradient                         | B\. Vlaisavljevich and T. Shiozaki J. Chem. Theory Comput. 12, 3781 (2016)      | 
+-----------------------------------------------+---------------------------------------------------------------------------------+
| (X)MS-CASPT2 derivative coupling              | J\. W. and T. Shiozaki, Submitted.                                              | 
+-----------------------------------------------+---------------------------------------------------------------------------------+

General References
------------------

+-----------------------------------------------+--------------------------------------------------------------------------------+
|          Description of Reference             |                          Reference                                             | 
+===============================================+================================================================================+
| General review of gradient methods            | Pulay, P. WIREs Comput. Mol. Sci. 2014, 4, 169-181.                            |
+-----------------------------------------------+--------------------------------------------------------------------------------+

