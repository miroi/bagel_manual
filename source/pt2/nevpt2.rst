.. index:: nevpt2

.. _nevpt2:

*****************************************************
N-electron valence state perturbation theory (NEVPT2)
*****************************************************


Description
===========
Calculations using the strongly contracted state-specific n-electron valence state perturbation theory (NEVPT2) 
are done using the keyword ``"title" : "nevpt2"``.

Keywords
========

The default values are recommended unless mentioned otherwise.

.. topic:: ``frozen``

   | **Description:** to have frozen orbitals or not
   | **Default:** true.
   | **Datatype:** bool

.. topic:: ``ncore``
   
   | **Description**: manually specify number of frozen orbitals, used when 'frozen' is turned on with ``"frozen" : "true"``.
   | **Datatype**: int

.. topic:: ``aux_basis``
   
   | **Description**: specify an alternative density fitting basis set for NEVPT2. If ``aux_basis`` is not
                      specified, the same density fitting basis used for the SCF reference (using the keyword ``df_basis``)
                      will be used.
   | **Default**: use the same density fitting basis as in molecule/df_basis.
   | **Datatype**: string

.. topic:: ``norm_thresh``
     
   | **Default**: 1.0e-13
   | **Datatype**: double 

.. topic:: ``istate``
   
   | **Description**: specific state used in the evaluation of the dynamical correlation 
   | **Default**: 0
   | **Datatype**: integer 

Example
=======

.. code-block:: javascript 

   { "bagel" : [
   
   {
     "title" : "molecule",
     "symmetry" : "C1",
     "basis" : "svp",
     "df_basis" : "svp-jkfit",
     "angstrom" : true,
     "geometry" : [
       { "atom" : "O",  "xyz" : [    0.00000000000,     -0.00000000000,      0.000000000000]},
       { "atom" : "H",  "xyz" : [    1.45860189536,     -0.00000000000,      0.504283963824]},
       { "atom" : "H",  "xyz" : [    0.75860194558,     -0.00000000000,     -0.504283963824]}
     ]
   },
   
   {
     "title" : "nevpt2",
     "nact_cas" : 2,
     "nclosed" : 4,
     "frozen" : true,
     "thresh" : 1.0e-8,
     "thresh_scf" : 1.0e-8,
     "thresh_fci" : 1.0e-10
   }
   
   ]}

References
==========

BAGEL references
----------------
+-----------------------------------------------+-----------------------------------------------------------------------+
|          Description of Reference             |                          Reference                                    | 
+===============================================+=======================================================================+
| Relativistic implementation of NEVPT2 in      | T\. Shiozaki and W. Mizukami, J. Chem. Theory Comput. **11**, 4733    |
| BAGEL                                         | (2015).                                                               |
+-----------------------------------------------+-----------------------------------------------------------------------+

General references
------------------

+-----------------------------------------------+-----------------------------------------------------------------------+
|          Description of Reference             |                          Reference                                    | 
+===============================================+=======================================================================+
| Original references for NEVPT2                | C\. Angeli, R. Cimiraglia, S. Evangelisti, T. Leininger, and J.-P.    |
|                                               | Malrieu, J. Chem. Phys. **114**, 10252 (2011).                        |
+-----------------------------------------------+-----------------------------------------------------------------------+
|                                               | C\. Angeli, R. Cimiraglia, and J.-P. Malrieu, J. Chem. Phys. **117**, |
|                                               | 9138 (2012).                                                          |
+-----------------------------------------------+-----------------------------------------------------------------------+

