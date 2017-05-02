.. _dimer_linked:

Description
===========
It is the constructor of covalently linked dimer. Dimer orbitals are localized first, then assigned to fragments.


Keywords
========

.. topic:: ``dimerize``
   
   | **Description:** start construting dimer

.. topic:: ``form``
   
   | **Description:** 
   | **Datatype:**
   | **Value**
   |  * linked
   |  * displace

.. topic:: ``dimer_active``

   | **Description:** specify monomer active orbitals
   | **Datatype:** set<int>

.. topic:: ``hf``

   | **Description:** dimer restricted Hartree-Fock calculation options
   | **Default:** use the same options as monomer (add hyperlink here :: RHF) calculations

.. topic:: ``localization``

   | **Description:** localize dimer molecular orbitals
   | **Default:** use default (add hyperlink here :: Localization)
  
.. topic:: ``scheme``

   | **Description:** options to assign dimer active orbitals
   | **Datatype:** string
   | **Values:** 
   |   ``active_first``: pick active space from dimer orbitals first, then attempt to localize
   |   ``localize_first``: localize dimer orbitals, then pick the active space within each fragment
   | **Default:** active_first

.. topic:: ``active_thresh``
   
   | **Description:** threshold overlap for obitals to be treated as active
   | **Datatype:** double
   | **Default:** 0.5


Prerequisite
============
(add hyperlink here :: RHF) calculations are needed to obtain fragment active orbitals.


