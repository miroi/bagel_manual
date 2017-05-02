.. _molecule:

*******
Molecule 
*******

===========
Description
===========
Molecule is one of the basic blocks to specify information, such as basis sets and geometry for the input system.

========
Keywords
========
.. topic:: ``basis``

   | DESCRIPTION: basis sets for the system
   | DEFAULT: No Default Value
   | DATATYPE: string
   | VALUES:
   |    Please refer to `Basis Sets`_ for possible aruments
   | RECOMMENDATION: None

.. topic:: ``df_basis``

   | DESCRIPTION: basis sets used for density fitting
   | DEFAULT: No Default Value
   | DATATYPE: string
   | VALUES:
   |     Please refer to `Auxiliary basis sets`_ for possible aruments
   | RECOMMENDATION: None

.. topic:: ``angstrom``

   | DESCRIPTION: specify units for atomic coordinates  
   | DEFAULT: false
   | DATATYPE: bool
   | VALUES:
   |    ``TRUE``: use angstrom
   |    ``FALSE``: use atomic units
   | RECOMMENDATION: None

.. topic:: ``geometry``

   | DESCRIPTION: specify elements and their Cartisian coordinates  
   | DEFAULT: No Default
   | DATATYPE: vector
   | VALUES: 
   |    Elements are specified as {"atom" : "Atom Name",  "xyz" : [x y z]}
   | RECOMMENDATION: None

.. topic:: ``molden_file``

   | DESCRIPTION: filename of input molden file
   | DEFAULT: No Default
   | DATATYPE: string
   | VALUE:
   |    User defined
   | RECOMMENDATION: None

=======
Example
=======

.. code-block:: javascript 

   { "bagel" : [

   {
     "title" : "molecule",
     "basis" : "svp",
     "df_basis" : "svp-jkfit",
     "angstrom" : false,
     "geometry" : [
         {"atom" : "H", "xyz" : [ -0.22767998367, -0.82511994081,  -2.66609980874]; },
         {"atom" : "O", "xyz" : [  0.18572998668, -0.14718998944,  -3.25788976629]; },
         {"atom" : "H", "xyz" : [  0.03000999785,  0.71438994875,  -2.79590979943]; }
     ]
   },

   {
     "title" : "hf",
     "thresh" : 1.0e-10
   }

   ]}

==========
Basis sets 
==========
* sto-3g
* 3-21g  
* 6-31g
* svp
* tzvpp
* qzvpp
* cc-pvdz  
* cc-pvtz  
* cc-pvqz
* cc-pv5z  
* cc-pv6z  
* aug-cc-pvdz
* aug-cc-pvtz
* aug-cc-pvqz
* aug-cc-pv5z
* aug-cc-pv6z
* ano-rcc
* ecp10mdf
* ecp28mdf
* ecp46mdf
* ecp60mdf
* ecp78mdf
* def2-SVP-ecp
* def2-SVP-2c-ecp
* lanl2dz-ecp
* molden ( :any:`molden_file` is required)

==========
Auxiliary basis sets
==========
* svp-jkfit
* tzvpp-jkfit
* qzvpp-jkfit
* cc-pvdz-jkfit
* cc-pvqz-jkfit
* cc-pvtz-jkfit
* cc-pv5z-jkfit
* cc-pvdz-ri
* cc-pvqz-ri
* cc-pvtz-ri
* cc-pv5z-ri
