.. _mp2:

****************************************
Møller–Plesset perturbation theory (MP2)
****************************************


Description
===========
MP2 computes the Møller–Plesset perturbation theory second-order correction to the Hartree-Fock energy. (Resolution of the identity approximation algorithm) is implemented here. In BAGEL, MP2 only works with density fitting.


Keywords
========

.. topic:: ``frozen``

   | **Description**: to have frozen orbitals or not
   | **Default**: true
   | **Datatype**: bool

.. topic:: ``ncore``
   
   | **Description**: manually specify number of frozen orbitals, used when 'frozen' is turned on
   | **Datatype**: int

.. topic:: ``aux_basis``
   
   | **Description**: specify an auxiliary basis set for MP2
   | **Default**: use the same density fitting basis as in molecule/df_basis
   | **Datatype**: string
   | **Recommendation**: use MP2-fit auxiliary basis (auxiliary basis ends with 'ri')


Example
=======
This should be an example that is chemically relevant. There should be text explaining what the example is and why it's interesting.


Sample input
------------

.. code-block:: javascript 

   { "bagel" : [
   
   {
     "title" : "molecule",
     "basis" : "cc-pvdz",
     "df_basis" : "cc-pvdz-jkfit",
     "angstrom" : "true",
     "geometry" : [
       { "atom" : "C", "xyz" : [ -1.20433891360,  0.54285096106, -0.04748199659] },
       { "atom" : "C", "xyz" : [ -1.20543291352, -0.83826393986,  0.12432899108] },
       { "atom" : "C", "xyz" : [ -0.00000600000, -1.52953889027,  0.20833398505] },
       { "atom" : "C", "xyz" : [  1.20544091352, -0.83825393987,  0.12432799108] },
       { "atom" : "C", "xyz" : [  1.20433091360,  0.54284396106, -0.04748099659] },
       { "atom" : "C", "xyz" : [  0.00000400000,  1.23314191154, -0.13372399041] },
       { "atom" : "H", "xyz" : [ -2.13410484690,  1.07591192282, -0.12500499103] },
       { "atom" : "H", "xyz" : [ -2.13651384673, -1.37179190159,  0.18742198655] },
       { "atom" : "H", "xyz" : [  0.00000000000, -2.59646181374,  0.33932597566] },
       { "atom" : "H", "xyz" : [  2.13651384673, -1.37179290159,  0.18742198655] },
       { "atom" : "H", "xyz" : [  2.13410684690,  1.07591292282, -0.12500599103] },
       { "atom" : "H", "xyz" : [ -0.00000000000,  2.29608983528, -0.28688797942] }
     ]
   },
   
   {
     "title" : "mp2",
     "aux_basis" : "cc-pvdz-ri",
     "frozen" : true
   }
   
   ]}




Some information about the output should also be included. This will not be entire output but enough for the reader to know their calculation worked.

.. figure:: ../figure/example.png
    :width: 200px
    :align: center
    :alt: alternate text
    :figclass: align-center

    This is an example of how to insert a figure. 

References
==========

+-----------------------------------------------+-----------------------------------------------------------------------+
|          Description of Reference             |                          Reference                                    | 
+===============================================+=======================================================================+
| Original reference for MP2                    | Møller C., Plesset M. S., Phys. Rev. **46**, 618 (1934)               |
+-----------------------------------------------+-----------------------------------------------------------------------+

