.. _molecule:

*******
Molecule 
*******

===========
Description
===========
Molecule is one of the basic blocks to specify information, such as basis sets and geometry for the input system.


=============
Pre-requisite
=============
None

========
Keywords
========
.. topic:: ``basis``
   | DESCRIPTION: basis sets for the system
   | DEFAULT: No Default Value
   | DATATYPE: string
   | VALUES:
   |    Please refer to $BAGEL_HOME/src/basis for possible aruments
   | RECOMMENDATION:
.. topic:: ``df_basis``
   | DESCRIPTION: basis sets used for density fitting
   | DEFAULT: No Default Value
   | DATATYPE: string
   | VALUES:
   |     Please refer to $BAGEL_HOME/src/basis for possible aruments
   | RECOMMENDATION:
.. topic:: ``angstrom``
   | DESCRIPTION: specify units for atomic coordinates
   | DEFAULT: false
   | DATATYPE: bool
   | VALUES:
   |    ``TRUE``: use angstrom
   |    ``FALSE``: use atomic units
   | RECOMMENDATION: NONE
.. topic:: ``geometry``
   | DESCRIPTION: specify elements and their Cartisian coordinates  
   | DEFAULT: No Default
   | DATATYPE: vector 
   | VALUES: {"atom" : "Atom Name",  "xyz" : [x y z]}
   | RECOMMENDATION: None

=======
Example
=======
This should be an example that is chemically relevant. There should be text explaining what the example is and why it's interesting.

============
Sample input
============

.. code-block:: javascript 
{
molecule = { 
  symmetry = C1; 
  basis = sto-3g;
  df_basis = svp;
  angstrom = true;
  geometry = [ 
    {atom = H; xyz = [ -0.22767998367, -0.82511994081,  -2.66609980874]; },
    {atom = O; xyz = [  0.18572998668, -0.14718998944,  -3.25788976629]; },
    {atom = H; xyz = [  0.03000999785,  0.71438994875,  -2.79590979943]; }
  ];  
};
}

==========
References
==========


