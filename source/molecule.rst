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
3-21g
6-31g
ano-rcc
aug-cc-pv5z
aug-cc-pv6z
aug-cc-pvdz
aug-cc-pvqz
aug-cc-pvtz
cc-pv5z
cc-pv5z-ri
cc-pv6z
cc-pvdz
cc-pvdz-ri
cc-pvqz
cc-pvqz-ri
cc-pvtz
cc-pvtz-ri
complete
def2-SVP-2c-ecp
def2-SVP-ecp
ecp10mdf
ecp28mdf
ecp46mdf
ecp60mdf
ecp78mdf
lanl2dz-ecp
qzvpp
sto-3g
svp
tzvpp

==========
Density fitting basis sets
==========
svp-jkfit
tzvpp-jkfit
cc-pv5z-jkfit
cc-pvdz-jkfit
cc-pvqz-jkfit
cc-pvtz-jkfit
qzvpp-jkfit


==========
References
==========

