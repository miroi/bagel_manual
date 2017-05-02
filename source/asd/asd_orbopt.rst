.. _asd_orbopt:

************************
ASD Orbital Optimization
************************


Description
===========
Description to ASD orbital optimization


Keywords
========

.. topic:: ``active orbitals``
   
   | **Description**: assign active orbitals


Example
=======
Give an example here


Sample input
------------

.. code-block:: javascript
   
   { "bagel" : [
   
   {
     "title" : "molecule",
     "symmetry" : "C1",
     "basis" : "sto-3g",
     "df_basis" : "svp",
     "angstrom" : true,
     "cartesian" : false,
     "geometry" : [
        {"atom" :"C", "xyz" : [       0.0000000    ,  0.0000000,      1.3976222  ] },
        {"atom" :"C", "xyz" : [       1.2106030    ,  0.0000000,      0.6988717  ] },
        {"atom" :"C", "xyz" : [       1.2105988    ,  0.0000000,      -0.6988913 ] },
        {"atom" :"C", "xyz" : [       0.0000000    ,  0.0000000,      -1.3976349 ] },
        {"atom" :"C", "xyz" : [       -1.2105988   ,  0.0000000,      -0.6988913 ] },
        {"atom" :"C", "xyz" : [       -1.2106030   ,  0.0000000,      0.6988717  ] },
        {"atom" :"H", "xyz" : [       2.1549225    ,  0.0000000,      1.2444381  ] },
        {"atom" :"H", "xyz" : [       2.1549235    ,  0.0000000,      -1.2444302 ] },
        {"atom" :"H", "xyz" : [       0.0000000    ,  0.0000000,      -2.4881454 ] },
        {"atom" :"H", "xyz" : [       -2.1549235   ,  0.0000000,      -1.2444302 ] },
        {"atom" :"H", "xyz" : [       -2.1549225   ,  0.0000000,      1.2444381  ] },
        {"atom" :"H", "xyz" : [       0.0000000    ,  0.0000000,      2.4881808  ] }
     ]
   },
   
   {
     "title" : "hf"
   },
   
   {
     "title" : "dimerize",
     "angstrom" : true,
     "translate" : [ 0.5, 2.8, 0.0],
     "dimer_active" : [ 17 ,20, 21, 22, 23, 24 ],
     "hf" : {
       "thresh" : 1.0e-10
     },
     "localization" : {
       "max_iter" : 50,
       "thresh" : 1.0e-8
     }
   },
   
   {
     "title" : "asd_orbopt",
     "algorithm" : "bfgs",
     "maxiter" : 100,
     "gradient_thresh" : 5.0e-7,
     "asd" : {
       "method" : "ras",
       "thresh" : 5.0e-8,
       "store_matrix" : false,
       "space_a" : [
         { "charge" : 0, "spin" : 0, "nstate" :8},
         { "charge" : 0, "spin" : 2, "nstate" :8},
         { "charge" : 1, "spin" : 1, "nstate" :8},
         { "charge" :-1, "spin" : 1, "nstate" :8}
       ],
       "space_b" : [
         { "charge" : 0, "spin" : 0, "nstate" :8},
         { "charge" : 0, "spin" : 2, "nstate" :8},
         { "charge" : 1, "spin" : 1, "nstate" :8},
         { "charge" :-1, "spin" : 1, "nstate" :8}
       ],
       "restricted" : [ {
         "orbitals" : [2,2,2],
         "max_holes" : 4,
         "max_particles" : 4
       } ],
       "ras" : {
         "thresh" : 5.0e-8,
         "nguess" : 400
       },
       "nstates" : 2,
       "spin" : 1,
       "charge" : 1
     }
   }
   
   ]}



Reference
=========
