.. _asd_orbopt:

************************
ASD orbital optimization
************************


Description
===========
Active space decomposition with orbital optimization is implemented. The two fragments of the molecule can be covalently linked, but the bridging orbitals cannot be active. Orbital rotations between active subspaces are included to partition the total active space into subspaces. The two active subspaces should be well separated. The calculation starts with dimer construction which is slightly different from that in :ref:`dimer_asd`.


Dimer Construction
==================
.. toctree:: 
   :maxdepth: 1

   dimer.rst


Keywords
========

Required Keywords
-----------------

.. topic:: ``asd_orbopt``
   
   | **Description:** asd calculation for covalently linked molecular dimer

.. topic:: ``algorithm``
   
   | **Description:** 'bfgs' orbital optimization algorithm is implemented
   | **Datatype:** string
   | **Value:** bfgs

.. topic:: ``maxiter``
   
   | **Description:** maximum number of orbita optimizatin iterations
   | **Datatype:** int
   | **Default:** 50

.. topic:: ``asd``

   | **Description:** asd information
   | **Recommendation:** see :ref:`dimer_asd` for details

.. topic:: ``gradient_thresh``
   
   | **Description:** threshold for calculating gradient
   | **Datatype:** double
   | **Default:** 0.0001
   | **Recommendation:** use default

.. topic:: ``rotation_thresh``
   
   | **Description:** threshold for orbital rotation
   | **Datatype:** double
   | **Default:** 0.0001
   | **Recommendation:** use default

.. topic:: ``energy_thresh``
   
   | **Description:** convergence threshold for calculating energy 
   | **Datatype:** double
   | **Default:** :math:`1.0\times 10^{-6}`
   | **Recommendation:** use default

.. topic:: ``semi-canonicalize``
   
   | **Description:** whether to semi-canonicalize localized orbitals
   | **Datatype:** bool
   | **Default:** false 


Reference
=========
+-----------------------------------------------+--------------------------------------------------------------------------------+
|          Description of Reference             |                          Reference                                             | 
+===============================================+================================================================================+
|  ASD orbital optimization                     | Kim I., Parker S. M., Shiozaki T., J. Chem. Theory Comput. **11**, 3636 (2015) |
+-----------------------------------------------+--------------------------------------------------------------------------------+

