========
pySettle
========

Build and installation from this github repository
--------------------------------------------------

This includes compilation of the underlaying C/C++ library (libsettle.so) and including it in the python package. On Linux, GCC development tools must be installed, on Mac, it works with clang compiler.

#. Clone the pysettle repository

   .. code-block::
    
      git clone https://github.com/adellej/pysettle
      cd pysettle
   

#. Create and activate a clean conda environment

   The example is for python 3.8, but should work for any version 3.6 to 3.11 as well.

   .. code-block::
    
      # remove existing environment if needed - to start from scratch
      conda remove -n settle-3.8 --all
      # create blank conda environment
      conda create --name settle-3.8 python==3.8.*
      conda activate settle-3.8

      
#. Install/upgarde pip, build and local install

   .. code-block::
  
      python3 -m pip install --upgrade pip
      python3 -m pip install --upgrade build

   .. code-block::
  
      # test build & local install
      # The "-e" install does not seem to be reliable for re-install 
      #       - keeps pulling some old build from somewhere middlewhere.
      # *Do not use:        python -m pip install -e .*
      # This is more reliable:
      python3 -m build
      python3 -m pip install .

   .. ::
   
   *Note: when workinng on the code, in case of doubts that recent changes got propagated, uninstall & purge the installed module _before_* ``pip install`` *to ensure the installed version has all the recent modifications.*

   .. code-block::
     
      python3 -m pip -v uninstall pySettle
      python3 -m pip -v cache purge

   After this, in that enviroment, pySettle just works from every directorty, providing the conda environment is activated.
   Imports like:

   .. code-block::
   
      from pySettle import settler

   (See `test_settle_sft.py <tests/test_settle_sft.py>`_.)


Run short functional test (SFT) manually
----------------------------------------

.. code-block::

   cd tests
   python ./test_settle_sft.py
 

Publish package on PyPI
----------------------------------------

.. code-block::

   python3 -m pip install twine

.. ::

**Test PyPI** : for testing that all works, but not yet really publishing to a place where all the world is searching for python packages.

.. code-block::

   python3 -m twine upload --repository testpypi dist/*

.. ::

**The Real PyPI**

.. code-block::

   python3 -m twine upload dist/*

.. ::


`pySettle on PyPI:  https://pypi.org/project/pySettle/ <https://pypi.org/project/pySettle/>`_
