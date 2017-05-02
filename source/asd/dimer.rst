.. _dimer:

Description
===========
The construction of the dimer molecule is separated from the ASD input block, it is built from one monomer by spatial translation. Then dimer active molecular orbitals are picked out by doing localization and comparing overlap with user-defined monomer active orbitals. Fragment wave functions are calculated within the active subspaces, whose linear combinations are used to construct the dimer wavefunction. 


Keywords
========

.. topic:: ``title``
   
   | **Value:** dimerize

.. topic:: ``translate``

   | **Description:** spatial distance in Cartesian coordinates
   | **Datatype:** array<double, 3>

.. topic:: ``angstrom`` 

   | **Description:** whether the translation is in a.u. or angstrom
   | **Datatype:** bool
   | **Default:** false

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


