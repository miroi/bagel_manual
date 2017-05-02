. _molecule:

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

   | **Description**: specify atoms and their Cartesian coordinates  
   | **Datatype**: vector
   | **Values**:
   |    Vector of atoms provided in the following format ``{ "atom" : "atom symbol",  "xyz" : [x, y, z] }``
        (see example below)

.. topic:: ``df_basis``

   | **Description**: basis sets used for density fitting
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

====================
User defined basis sets
====================

The basis set file is in the following format

.. code-block:: javascript 

 {
  "H" : [
    {
      "angular" : "s",
      "prim" : [5.4471780, 0.8245470],
      "cont" : [[0.1562850, 0.9046910]]
    }, {
      "angular" : "s",
      "prim" : [0.1831920],
      "cont" : [[1.0000000]]
    }
  ],
  "He" : [
    {
      "angular" : "s",
      "prim" : [13.6267000, 1.9993500],
      "cont" : [[0.1752300, 0.8934830]]
    }, {
      "angular" : "s",
      "prim" : [0.3829930],
      "cont" : [[1.0000000]]
    }
  ]
 }

| The file is essentially one large array, the elements of which are further arrays, each corresponding to the basis set for a given element.
| The basis set for associated with each element is then made up of futher arrays, each of which  contains information specifying the properties
of a single basis function.
| "angular" defines the kind of orbital (s,p,d,f...) . 
| "prim" is a array containing the exponents of the primative orbitals from which the basis funciton is composed.
| "cont" is an array containing the coefficients associated with each of these primiative orbitals.
|
| The user casn specify their own basis set using the above format, or use one of the predefined basis sets listed below. Note that not
all of the below basis sets are defined for all atome; an error of form "node does not exist" often means that the relevant element was not found in the basis set file.
 
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

====================
Auxiliary basis sets
====================
* cc-pv5z-ri
* cc-pvdz-ri
* cc-pvqz-ri
* cc-pvtz-ri

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



=======
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
