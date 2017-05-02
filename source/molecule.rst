.. _molecule:

*******
Molecule 
*******

===========
Description
===========
Molecule is one of the basic blocks to specify information, such as basis sets and geometry for the input system.


=============
Pre-requisite
=============
None

========
Keywords
========
.. topic:: ``basis``

   | DESCRIPTION: basis sets for the system
   | DEFAULT: No Default Value
   | DATATYPE: string
   | VALUES:
   |    Please refer to $BAGEL_HOME/src/basis for possible aruments
   | RECOMMENDATION:

.. topic:: ``df_basis``

   | DESCRIPTION: basis sets used for density fitting
   | DEFAULT: No Default Value
   | DATATYPE: string
   | VALUES:
   |     Please refer to $BAGEL_HOME/src/basis for possible aruments
   | RECOMMENDATION:

.. topic:: ``geometry``

   | DESCRIPTION: specify elements and their Cartisian coordinates  
   | DEFAULT: No Default
   | DATATYPE: vector
   | VALUES: {"atom" : "Atom Name",  "xyz" : [x y z]}
   | RECOMMENDATION: None

=======
Example
=======

Sample input
------------

.. code-block:: javascript 

   { "bagel" : [

   {
     "title" : "molecule",
     "basis" : "sto-3g",
     "df_basis" : "svp-jkfit",
     "angstrom" : false,
     "geometry" : [
         {atom = H; xyz = [ -0.22767998367, -0.82511994081,  -2.66609980874]; },
         {atom = O; xyz = [  0.18572998668, -0.14718998944,  -3.25788976629]; },
         {atom = H; xyz = [  0.03000999785,  0.71438994875,  -2.79590979943]; }
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
* 3-21g  
* 6-31g
* sto-3g
* svp
* cc-pv5z  
* cc-pv6z  
* cc-pvdz  
* cc-pvtz  
* cc-pvqz
* tzvpp
* qzvpp
* ano-rcc
* ecp10mdf
* ecp28mdf
* ecp46mdf
* ecp60mdf
* ecp78mdf
* def2-SVP-ecp
* def2-SVP-2c-ecp
* lanl2dz-ecp

==========
Density fitting basis sets
==========
* svp-jkfit
* cc-pv5z-ri
* cc-pvdz-ri
* cc-pvqz-ri
* cc-pvtz-ri
* tzvpp-jkfit
* qzvpp-jkfit
* cc-pv5z-jkfit
* cc-pvdz-jkfit
* cc-pvqz-jkfit
* cc-pvtz-jkfit
* aug-cc-pv5z
* aug-cc-pv6z
* aug-cc-pvdz
* aug-cc-pvtz
* aug-cc-pvqz

==========
References
==========

