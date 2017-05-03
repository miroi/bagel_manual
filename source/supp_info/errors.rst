.. _errors:

*********************
Common error messages
*********************

.. topic:: ``<filename.json>(#): expected key string``

   | An error occurrred when parsing a .json file.
   | Usually, there is a syntax error in your input file, such an extra comma where it does not belong.
   | These errors can also occur when reading custom basis set files.

.. topic:: ``<filename.json>(#): expected value``

   | Another syntax error in a .json file.  Very similar to the previous error message.

.. topic:: ``<filename.json>(#): expected ']' or ','``

   | Another syntax error in a .json file.  Usually, you are missing a comma between input keys.

.. topic:: ``EXCEPTION RAISED:No such node (<keyword>)``

   | The specified keyword is required for the method you have chosen, but is not found in the input file (or custom basis set).

.. topic:: ``EXCEPTION RAISED:input stream error``

   | An error occurred when boost's serialization library tried to read in a binary archive file.
   | Most commonly, this means you misspelled the directory or filename.
   | This error can also indicate that the archive is unreadable, possibly due to being generated with a different version of BAGEL.

.. topic:: ``EXCEPTION RAISED:output stream error``

   | An error occurred when boost's serialization library tried to write a binary archive file.
   | Most commonly, this means you misspelled the directory.
