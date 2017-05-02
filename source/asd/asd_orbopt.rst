.. _asd_orbopt:

************************
ASD orbital optimization
************************


Description
===========
Active space decomposition with orbital optimization is implemented. The two fragments of the molecule can be covalently bonded, but the bridging orbitals cannot be active. Orbital rotations between active subspaces are included to partition the total active space into subspaces. The two active subspaces should be well separated. The calculation starts with dimer construction which is slightly different from that in (add hyperlink to dimer_asd).


Dimer Construction
==================
.. toctree:: 
   :maxdepth: 1

   dimer_linked.rst


Keywords
========

Required Keywords
-----------------

.. topic:: ``asd``
   
   | **Description:** asd calculation for non-covalently bonded molecular dimer

.. topic:: ``method``
   
   | **Description:** method to compute active subspaces
   | **Datatype:** string
   | **Value:**
   |   ``cas``/``fci``: use full configuration interaction method
   |   ``ras``: use restricted active space configuration interaction method

.. topic:: ``fci``

   | **Description:** if ``fci`` is used, specify the implementations here
   | **Recommendation:** see (add hyperlink to fci) for details

.. topic:: ``ras``

   | **Description:** if ``ras`` is used, specify the implementations here
   | **Recommendation:** see (add hyperlink to ras) for details

.. topic:: ``space``

   | **Description:** specify important fragment states with the following keys:
   |  ``charge``, ``spin``, ``nstate``
   | **Recommendation:** see sample input for details

Optional Keywords
-----------------

.. topic:: ``nstates``
   
   | **Description:** number of target states
   | **Datatype:** int
   | **Default** 10

.. topic:: ``charge``

   | **Description:** dimer charge
   | **Datatype:** int
   | **Default:** 0

.. topic:: ``nspin``

   | **Description:** number of dimer total spin
   | **Datatype:** int
   | **Default:** 0

.. topic:: ``nguess``

   | **Description:** number of initial guess for Davidson diagonalization
   | **Datatype:** int
   | **Default** :math:`10\times nstates`

.. topic:: ``Davidson_subspace``
   
   | **Description:** size of Davidson subspace
   | **Datatype:** int
   | **Default:** 10

.. topic:: ``max_iter``
   
   | **Description:** maximum number of iterations for Davidson diagonalization 
   | **Datatype:** int
   | **Default:** 50

.. topic:: ``dipoles``
   
   | **Description:** whether to calculate dipole moment
   | **Datatype:** bool
   | **Default:** false

.. topic:: ``thresh``
   
   | **Description:** threshold for convergence in Davidson diagonalization
   | **Datatype:** double
   | **Default:** :math:`1.0\times 10^{-7}`

.. topic:: ``print_thresh``

   | **Description:** threshold for printing out important configurations
   | **Datatype:** double
   | **Default:** 0.01

.. topic:: ``store matrix``
   
   | **Description:** whether the Hamiltonian matrix is stored
   | **Datatye:** bool
   | **Default:** false

.. topic:: ``print_info``   
   
   | **Description:** whether print out information (e.g. reduced density matrix and energy)
   | **Datatype:** bool
   | **Default:** false


Example
=======
Here is a sample calculation of a benzene dimer molecule.

.. figure:: ../figure/benzene_dimer.png
    :width: 100px
    :align: center
    :alt: alternate text
    :figclass: align-center

Sample input
------------

.. code-block:: javascript


 
Reference
=========
+-----------------------------------------------+--------------------------------------------------------------------------------+
|          Description of Reference             |                          Reference                                             | 
+===============================================+================================================================================+


