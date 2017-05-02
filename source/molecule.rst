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

   | **Description**: define default basis set used for the system
   | **Datatype**: string
   | **Values**:
   |    Please refer to `Basis sets`_ and `Effective core potential (ECP) basis sets`_ for possible arguments

Note that the use of mixed basis sets is possible by specifying a different basis set other than the default
for each atom (see example for `Effective core potential (ECP) basis sets`_ below).

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
* aug-cc-pv5z
* aug-cc-pv6z
* aug-cc-pvdz
* aug-cc-pvtz
* aug-cc-pvqz
* ano-rcc

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

====================
Auxiliary basis sets
====================
* cc-pv5z-ri
* cc-pvdz-ri
* cc-pvqz-ri
* cc-pvtz-ri

Example
-------

An example using ``cc-pvdz-ri`` in MP2 calculation

.. code-block:: javascript 

   { "bagel" : [
   
   {
     "title" : "molecule",
     "basis" : "cc-pvdz",
     "df_basis" : "cc-pvdz-jkfit",
     "angstrom" : "true",
     "geometry" : [
       { "atom" : "C", "xyz" : [ -1.20433891360,  0.54285096106, -0.04748199659] },
       { "atom" : "C", "xyz" : [ -1.20543291352, -0.83826393986,  0.12432899108] },
       { "atom" : "C", "xyz" : [ -0.00000600000, -1.52953889027,  0.20833398505] },
       { "atom" : "C", "xyz" : [  1.20544091352, -0.83825393987,  0.12432799108] },
       { "atom" : "C", "xyz" : [  1.20433091360,  0.54284396106, -0.04748099659] },
       { "atom" : "C", "xyz" : [  0.00000400000,  1.23314191154, -0.13372399041] },
       { "atom" : "H", "xyz" : [ -2.13410484690,  1.07591192282, -0.12500499103] },
       { "atom" : "H", "xyz" : [ -2.13651384673, -1.37179190159,  0.18742198655] },
       { "atom" : "H", "xyz" : [  0.00000000000, -2.59646181374,  0.33932597566] },
       { "atom" : "H", "xyz" : [  2.13651384673, -1.37179290159,  0.18742198655] },
       { "atom" : "H", "xyz" : [  2.13410684690,  1.07591292282, -0.12500599103] },
       { "atom" : "H", "xyz" : [ -0.00000000000,  2.29608983528, -0.28688797942] }
     ]
   },
   
   {
     "title" : "mp2",
     "aux_basis" : "cc-pvdz-ri",
     "frozen" : true
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
