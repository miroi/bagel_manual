.. _multisite:

Description
===========
The constructor of molecular aggregate for ASD-DMRG algorithm.


Keywords
========

.. topic:: ``multisite``
   
   | **Description:** start construting multisite

.. topic:: ``refs``

   | **Description:** provide saved reference names
   | **Recommendation:** refer to sample input for details

.. topic:: ``active``
   
   | **Description:** specify single site active orbitals
   | **Datatype:** set<int>

.. topic:: ``hf``

   | **Description:** multisite restricted Hartree-Fock calculation options
   | **Default:** use the same options as single site (add hyperlink here :: RHF) calculations

.. topic:: ``localization``

   | **Description:** localize multisite molecular orbitals
   | **Default:** use default (add hyperlink here :: Localization)
   
   



Prerequisite
============
(add hyperlink here :: RHF) calculations are needed to obtain fragment orbitals.
