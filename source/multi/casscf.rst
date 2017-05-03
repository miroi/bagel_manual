.. index:: casscf

.. _casscf:

****************************************************
Complete active space self-consistent field (CASSCF)
****************************************************

Description
===========

CASSCF simultaneously optimizes the orbital coefficients and the CI coefficients of all the possible determinants generated from the active space.
The state-averaging scheme for calculating excited states is also implemented. When no orbitals are specified as a input to CASSCF calculation,
Hartree--Fock calculation is performed by default prior to CASSCF. For the Hartree--Fock options, see the SCF section.

The second-order algorithm is implemented in BAGEL. This algorithm is constructed of macroiterations and microiterations. At each macroiteration,
the CI coefficient is optimized by FCI calculations, while the orbitals are rotated in microiterations.

**The CASSCF algorithm in BAGEL is very robust. If it fails to converge, it is highly likely that your active space is wrong, or your guess orbitals are wrong.**

Command: ``casscf``

Keywords
========

.. topic:: ``nstate``

   | **Description:** Number of states included in the state averaging.
   | **Default:** 1.
   | **Datatype:** integer

.. topic:: ``nact``

   | **Description:** Number of active orbitals.
   | **Default:** 0.
   | **Datatype:** integer

.. topic:: ``nclosed``

   | **Description:** Number of closed orbitals.
   | **Default:** Number of electrons / 2.
   | **Datatype:** integer

.. topic:: ``active``

   | **Description:** Specify active orbitals. Note that the orbital index starts from 1.
   | **Default:** Nact / 2 orbitals lower and higher from the valence orbital.
   | **Example:**
   |    [36, 37, 39] : include 36th, 37th, and 39th orbitals.
   | **Datatype:** integer array

.. topic:: ``algorithm``

   | **Description:** Orbital optimization algorithm.
   | **Default:** ``second``
   | **Datatype:** string
   | **Values:**
   |    ``second``: second-order algorithm.
   |    ``noopt``: no orbital optimization.
   | **Recommendation:** use default.

.. topic:: ``fci_algorithm``

   | **Description:** FCI algorithm employed in each macroiteration.
   | **Default:** ``parallel`` (when the number of active orbital is larger than 9 and number of process is larger than 8), ``knowles`` (otherwise)
   | **Datatype:** string
   | **Values:**
   |    ``knowles``, ``handy``, ``kh``: Knowles--Handy Algorithm.
   |    ``harrison``, ``zarrabian``, ``hz``: Harrison--Zarrabian Algorithm.
   |    ``parallel``, ``dist``: Parallel FCI algorithm.
   | **Recommendation:** use default.

.. topic:: ``thresh``

   | **Description:** Convergence threshold in macroiteration.
   | **Default:** 1.0e-8.
   | **Datatype:** double precision
   | **Recommendation:** use default.

.. topic:: ``thresh_micro``

   | **Description:** Convergence threshold in microiteration.
   | **Default:** 5.0e-6.
   | **Datatype:** double precision
   | **Recommendation:** use default.

.. topic:: ``conv_ignore``

   | **Description:** Throw the calculation or not when the convergence is not reached.
   | **Default:** false.
   | **Datatype:** bool
   | **Values:**
   |    ``true``: Do not throw the calculation.
   |    ``false``: Throw the calculation.
   | **Recommendation:** use default.

.. topic:: ``natocc``

   | **Description:** Print natural orbitals or not.
   | **Default:** false.
   | **Datatype:** bool
   | **Values:**
   |    ``true``: Print natural orbitals.
   |    ``false``: Do not print natural orbitals.
   | **Recommendation:** use default.

.. topic:: ``maxiter``

   | **Description:** Maximum number of macroiteration.
   | **Default:** 50.
   | **Datatype:** integer
   | **Recommendation:** Increase if convergence is not obtained.

.. topic:: ``maxiter_micro``

   | **Description:** Maximum number of microiteration.
   | **Default:** 100.
   | **Datatype:** integer
   | **Recommendation:** use default.

Example
=======
Two-state CASSCF calculation of benzene. The active space of (6e,6o), which comprises three :math:`\pi` and three :math:`\pi^*` orbitals, is used.

Sample input
------------

.. code-block:: javascript

  { "bagel" : [

  {
    "title" : "molecule",
    "basis" : "svp",
    "df_basis" : "svp-jkfit",
    "geometry" : [
    { "atom" : "C", "xyz" : [     -0.079002,      2.543870,      0.000000 ] },
    { "atom" : "C", "xyz" : [      2.557470,      2.543870,      0.000000 ] },
    { "atom" : "C", "xyz" : [      3.875630,      4.826190,      0.000000 ] },
    { "atom" : "C", "xyz" : [      2.557250,      7.109950,     -0.002266 ] },
    { "atom" : "C", "xyz" : [     -0.078588,      7.109800,     -0.003171 ] },
    { "atom" : "C", "xyz" : [     -1.396870,      4.826620,     -0.001289 ] },
    { "atom" : "H", "xyz" : [     -1.117900,      0.744245,      0.000850 ] },
    { "atom" : "H", "xyz" : [      3.595900,      0.743875,      0.002485 ] },
    { "atom" : "H", "xyz" : [      5.953730,      4.826340,      0.001198 ] },
    { "atom" : "H", "xyz" : [      3.596980,      8.909240,     -0.002377 ] },
    { "atom" : "H", "xyz" : [     -1.118170,      8.909350,     -0.004972 ] },
    { "atom" : "H", "xyz" : [     -3.474820,      4.826960,     -0.001629 ] }
    ]
  },
  {
    "title" : "hf"
  },
  {
    "title" : "casscf",
    "nstate" : 2,
    "nact" : 6,
    "nclosed" : 18,
    "active" : [17, 20, 21, 22, 23, 30]
  }
  ]}

The specified active orbitals are printed in the output:

.. code-block:: javascript

  ---------------------------
      CASSCF calculation
  ---------------------------

  ==== Active orbitals : =====
       Orbital 17
       Orbital 20
       Orbital 21
       Orbital 22
       Orbital 23
       Orbital 30
  ============================

This converges in five macroiterations.


References
==========

The second-order orbital optimization is implemented with an assistance of Takeshi Yanai (Institute for Molecular Science, Japan).
