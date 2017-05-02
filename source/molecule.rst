.. _molecule:

********
Molecule 
********

===========
Description
===========
Molecule, starting with ``"title" : "molecule"``, is one of the basic input blocks specifying important
information such as basis sets and geometry for the input system.

=================
Required keywords
=================
.. topic:: ``basis``

   | **Description**: basis sets for the system
   | **Datatype**: string
   | **Values**:
   |    Please refer to `Basis sets`_ and `Effective core potential (ECP) basis sets`_ for possible arguments

.. topic:: ``geometry``

   | **Description**: specify elements and their Cartisian coordinates  
   | **Default**: No Default
   | **Datatype**: vector
   | **Values**: 
   |    Elements are specified as {"atom" : "Atom Name",  "xyz" : [x y z]}

.. topic:: ``df_basis``

   | **Description**: basis sets used for density fitting
   | **Default**: No Default Value
   | **Datatype**: string
   | **Values**:
   |     Please refer to `Density fitting basis sets`_ for possible arguments

=================
Optional keywords
=================

.. topic:: ``angstrom``

   | **Description**: specify units for atomic coordinates (Angstrom or Bohr)
   | **Default**: false (Angstrom)
   | **Datatype**: bool
   |    ``TRUE``: use Angstrom
   |    ``FALSE``: use Bohr

.. topic:: ``molden_file``

   | **Description**: filename of input molden file"
   | **Default**: No Default
   | **Datatype**: string

.. topic:: ``schwarz_thresh``

   | **Description**: Schwarz screening integral threshold
   | **Default**: :math:`1.0\times 10^{-12}`
   | **Datatype**: double 

.. topic:: ``cfmm``

   | **Description**: option to do RHF-FMM, in which case density fitting is not used
   | **Default**: false 
   | **Datatype**: boolean 

==========
Basis sets 
==========
* 3-21g  
* 6-31g
* sto-3g
* svp
* tzvpp
* qzvpp
* cc-pv5z  
* cc-pv6z  
* cc-pvdz  
* cc-pvtz  
* cc-pvqz
* cc-pv5z-ri
* cc-pvdz-ri
* cc-pvqz-ri
* cc-pvtz-ri
* aug-cc-pv5z
* aug-cc-pv6z
* aug-cc-pvdz
* aug-cc-pvtz
* aug-cc-pvqz
* ano-rcc
* molden ( :any:`molden_file` is required)

==========================
Density fitting basis sets
==========================
* svp-jkfit
* tzvpp-jkfit
* qzvpp-jkfit
* cc-pv5z-jkfit
* cc-pvdz-jkfit
* cc-pvqz-jkfit
* cc-pvtz-jkfit

Example
-------

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

=========================================
Effective core potential (ECP) basis sets 
=========================================
* ecp10mdf
* ecp28mdf
* ecp46mdf
* ecp60mdf
* ecp78mdf
* def2-SVP-ecp
* def2-SVP-2c-ecp
* lanl2dz-ecp

Example
-------

Example for CuH2 using cc-pvtz basis set for H and lanl2dz-ecp for the heavy atom Cu

.. code-block:: javascript 

   { "bagel" : [
   
   {
     "title" : "molecule",
     "symmetry" : "C1",
     "basis" : "lanl2dz-ecp",
     "df_basis" : "svp-jkfit",
     "angstrom" : "true",
     "geometry" : [
       { "atom" : "Cu",  "xyz" : [  0.000000,      0.000000,      0.000000]},
       { "atom" :  "H",  "xyz" : [  0.000000,      0.000000,     -1.560000],
                        "basis" : "cc-pvtz"},
       { "atom" :  "H",  "xyz" : [  0.000000,      0.000000,      1.560000],
                        "basis" : "cc-pvtz"}
     ]
   },
   
   {
     "charge" : "-1",
     "title" : "hf",
     "thresh" : 1.0e-8
   }
   
   ]}
