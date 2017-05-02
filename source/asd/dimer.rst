.. _dimer:

Description
===========
The constructor of dimer molecule. The dimer fragments can either be covalently linked or not. The active subspaces should be well separated.


Keywords
========

Common keywords
---------------

.. topic:: ``title``
   
   | **Value:** dimerize

.. topic:: ``form``
   
   | **Description:** whether the dimer fragments are covalently linked
   | **Datatype:** string
   | **Value:**
   |  * linked: covalently linked dimer
   |  * displace: separated fragments
   | **Default:** displace

.. topic:: ``dimer_active``

   | **Description:** 
   |  * for non-covalently linked dimer: specify monomer active orbitals, 
   |  * for covalently linked dimer: specify dimer active orbitals, 
   | **Datatype:** set<int>

.. topic:: ``hf``

   | **Description:** dimer restricted Hartree-Fock calculation options
   | **Default:** use the same options as monomer :ref:`hf` calculations

.. topic:: ``localization``

   | **Description:** localize dimer molecular orbitals
   | **Default:** use default :ref:`localization`

.. topic:: ``active_thresh``
   
   | **Description:** threshold overlap for obitals to be treated as active
   | **Datatype:** double
   | **Default:** 0.5

Keywords for non-covalently linked dimer
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

Keywords for covalently linked dimer
----------------------------------------

.. topic:: ``region_sizes``
   
   | **Description:** number of atoms in three regions [left, bridge, right]
   | **Datatype:** vector<int>


Prerequisite
============
:ref:`hf` calculations are needed to obtain fragment active orbitals.

