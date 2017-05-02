.. index:: ci

.. _ci:

******************************************
Configuration interaction 
******************************************

This section discusses three of the closely related configuration interaction (CI) methods available in BAGEL; non-relativistic full configuration interaction (FCI) , restricted active space configuration interaction, and relativistic full configuration interaction (RelFCI).  These methods have many similarities, but substantial difference in their use. Accordingly, each shall be discussed in a different subsection. Note that keywords which work for one method may not work in another.

Most of the relevant code for these methods can be found in 
BAGEL/src/ci/ci (FCI) ,   
BAGEL/src/ci/ras (RASCI), 
BAGEL/src/ci/zfci (ZFCI).


.. toctree::
   :maxdepth: 1

   fci.rst 
   zfci.rst 
   rasci.rst  

