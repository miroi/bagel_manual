.. _zcasscf:

********************************************************************
Relativistic complete active space self-consistent field (RelCASSCF)
********************************************************************

Description
===========
The relativistic analogue of CASSCF is implemented in BAGEL. The second-order algorithm which is basically the same as its non-relativistic analogue is used by default.

Command: ``zcasscf``

Keywords
========
.. topic:: ``state``

   | **Description**: Number of states computed for each spin value.  All are included in the state-averaging procedure when orbitals are optimized.
   | **Datatype**: vector<int>
   | **Default**:  There is no default; this parameter must be supplied in the input.
   | **Note**:  An array of integers is supplied, where each one indicates the number of states for a given spin value.  For example,
   |      the input [ 1 ] gives a singlet ground state, while [ 3, 0, 1 ] gives three singlets and one triplet (6 states total).
   |      Be careful!  While the spin values you specified are used in generating guess CI coefficients, the spin sectors will mix, and the
   |      algorithm returns the *n* lowest eigenstates regardless of their spin expectation values.

.. topic:: ``nact``

   | **Description**: Number of active orbitals
   | **Datatype**: int
   | **Default**: 0

.. topic:: ``nclosed``

   | **Description**:  Number of closed orbitals
   | **Datatype**: int
   | **Default**: Number of electrons / 2. 

.. topic:: ``active``

   | **Description:** Specify active orbitals. Note that the orbital index starts from 1.
   | **Datatype:** vector<int>
   | **Default:** Nact / 2 orbitals lower and higher from the valence orbital.
   | **Example:**
   |    [36, 37, 39] : include 36th, 37th, and 39th orbitals.

.. topic:: ``algorithm``

   | **Description:** Orbital optimization algorithm.
   | **Datatype:** string
   | **Values:**
   |    ``second``: second-order algorithm.
   |    ``noopt``: no orbital optimization.
   | **Default:** ``second``

.. topic:: ``gaunt``

   | **Description**:  Used to specify the form of the 2-electron Hamiltonian used.  The default is to use the Dirac--Coulomb Hamiltonian;
   |     If "gaunt" is set to true, the Gaunt interaction will be added, which accounts for direct spin--spin and spin-other-orbit
   |     coupling between electrons.
   | **Datatype**: bool
   | **Default**: Value obtained from reference wavefunction.
   | **Recommendation**:  Choose based on the importance of relativistic effects for your problem.

.. topic:: ``breit``

   | **Description**:  Used to determine whether the full Breit interaction (including the gauge term) is included in the two-electron Hamiltonian.
   | **Datatype**: bool
   | **Default**: Value obtained from reference wavefunction.
   | **Recommendation**:  Choose based on the importance of relativistic effects for your problem.

.. topic:: ``only_electrons``

   | **Description**:  This option allows the user to freeze all positronic orbitals and optimize only for rotations between electronic orbitals.
   | **Datatype**: bool
   | **Default**:   false

.. topic:: ``natocc``

   | **Description**: If set to "true," occupation numbers of natural orbitals within the active space will be printed to casscf.log after each macroiteration.
   | **Datatype**: bool
   | **Default**: false

.. topic:: ``charge``

   | **Description**:  Molecular charge.
   | **Datatype**: int
   | **Default**: 0

.. topic:: ``hcore_guess``

   | **Description**:  If set to true, the one-electron Hamiltonian is diagonalized to generate initial guess orbitals.
   | **Datatype**: bool
   | **Default**: false

.. topic:: ``maxiter``

   | **Description**: Maximum number of macroiterations.
   | **Datatype**: int
   | **Default**: 100

.. topic:: ``maxiter_micro``

   | **Description**: Maximum number of microiterations.
   | **Datatype**: int
   | **Default**: 20 

.. topic:: ``maxiter_fci``

   | **Description**: Maximum number of iterations in CI coefficient optimization 
   | **Datatype**: int
   | **Default**: copied from ``maxiter``

.. topic:: ``thresh_fci``

   | **Description**: Convergence threshold for the CI coefficients
   | **Datatype**: double
   | **Default**: Value copied from ``thresh``

.. topic:: ``conv_ignore``

   | **Description:**  If set to "true," BAGEL will continue running even if the maximum iterations is reached without convergence.  Normally an error is thrown and the program terminates.  
   | **Datatype:** bool
   | **Default:** false.

.. topic:: ``pop``

   | **Description**: If set to true, population analysis of the molecular orbitals will be printed to a file names dhf.log.
   | **Datatype**: bool
   | **Default**: false

.. topic:: ``davidson_subspace``

   | **Description**:  Number of vectors retained in the limited-memory Davidson algorithm.
   | **Datatype**: int
   | **Default**: 20
   | **Recommendation**: Reduce if an insufficient amount of memory is available (do not reduce to a value lower than 3). 

.. topic:: ``print_thresh``

   | **Description**: Threshold below which CI coefficients are not printed.  
   | **Datatype**: double
   | **Default**: 0.05

.. topic:: ``spin_adapt``

   | **Description**: Spin-adapt the starting guess. 
   | **Datatype**: bool
   | **Default**: true
   | **Recommendation**: Use false if the error "generate_guess produced an invalid determinant" is generated. 

.. topic:: ``aniso``

   | **Description**: Performs magnetic anisotropy analysis (g-factors and zero-field splitting parameters). 
   | **Datatype**: int

Example
=======

References
==========

BAGEL references
----------------
+-----------------------------------------------+-----------------------------------------------------------------------+
|          Description of Reference             |                          Reference                                    |
+===============================================+=======================================================================+
| Extension to permit external magnetic fields, | R\. D. Reynolds and T. Shiozaki, Phys. Chem. Chem. Phys. **17**,      |
| including GIAO-RMB atomic basis.              | 14280 (2015).                                                         |
+-----------------------------------------------+-----------------------------------------------------------------------+

General references
------------------
+-----------------------------------------------+-----------------------------------------------------------------------+
|          Description of Reference             |                          Reference                                    |
+===============================================+=======================================================================+
| General text on relativistic electronic       | M\. Reiher and A. Wolf, *Relativistic Quantum Chemistry* (Wiley-VCH,  |
| structure, including Dirac--Hartree--Fock.    | Weinheim, 2009).                                                      |
+-----------------------------------------------+-----------------------------------------------------------------------+
