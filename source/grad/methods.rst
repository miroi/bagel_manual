.. _methods:

****************************************
Description of input structure   
****************************************

Description
===========
The force section can be used to compute the analytical gradient (force), the numerical gradient by finite difference, or the non-adiabatic coupling matrix elements (NACME). Analytical gradients are implemented for unrestricted Hartree–Fock (UHF), restricted open-shell Hartree–Fock (ROHF), restricted Hartree–Fock (RHF), Dirac–Hartree–Fock (DHF), Moller–Plesset perturbation theory (MP2), complete active space self consistent field (CASSCF), and multireference perturbation theory (CASPT2). 

Method Array
============
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
          "title" : "smith",
          "method" : "caspt2",
          "shift" : 0.2,
          "frozen" : true
        } 
      ]
  }

