.. _dimer:

Description
===========
The constructor of dimer molecule. The dimer fragments can either be covalently bonded or not. The active subspaces should be well separated.


Keywords
========

Common keywords
---------------

.. topic:: ``title``
   
   | **Value:** dimerize

.. topic:: ``dimer_active``

   | **Description:** 
   |  * for non-covalently bonded dimer: specify monomer active orbitals, 
   |  * for covalently bonded dimer: specify dimer active orbitals, 
   | **Datatype:** set<int>

.. topic:: ``hf``

   | **Description:** dimer restricted Hartree-Fock calculation options
   | **Default:** use the same options as monomer (add hyperlink here :: RHF) calculations

.. topic:: ``localization``

   | **Description:** localize dimer molecular orbitals
   | **Default:** use default (add hyperlink here :: Localization)

.. topic:: ``active_thresh``
   
   | **Description:** threshold overlap for obitals to be treated as active
   | **Datatype:** double
   | **Default:** 0.5

Keywords for non-covalently bonded dimer
----------------------------------------

.. topic:: ``translate``

   | **Description:** spatial distance in Cartesian coordinates, duplicate and translate one monomer to form the dimer
   | **Datatype:** array<double, 3>

.. topic:: ``angstrom`` 

   | **Description:** whether the translation is in a.u. or angstrom
   | **Datatype:** bool
   | **Default:** false

.. topic:: ``scheme``

   | **Description:** options to assign dimer active orbitals
   | **Datatype:** string
   | **Values:** 
   |   ``active_first``: pick active space from dimer orbitals first, then attempt to localize
   |   ``localize_first``: localize dimer orbitals, then pick the active space within each fragment
   | **Default:** active_first

Keywords for covalently bonded dimer
----------------------------------------

.. topic:: ``form``
   
   | **Description:** 
   | **Datatype:**
   | **Value**
   |  * linked
   |  * displace





  


Prerequisite
============
(add hyperlink here :: RHF) calculations are needed to obtain fragment active orbitals.


