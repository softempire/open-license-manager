#######################################
C++ software protection with Licensecc
#######################################
Copy protect, restrict the usage of your C++ software with a license file using this library.

|c11|_ |License|_ |unstable|_ |BuildStatus|_ |CodacyBadge|_ |codecov|_ |forum|_ 

.. |c11| image:: https://img.shields.io/badge/c%2B%2B-11-blue.svg
.. _c11: https://en.wikipedia.org/wiki/C%2B%2B#Standardization
.. |unstable| image:: http://badges.github.io/stability-badges/dist/unstable.svg
.. _unstable: http://github.com/badges/stability-badges
.. |License| image:: https://img.shields.io/badge/License-BSD%203--Clause-blue.svg
.. _License: ttps://opensource.org/licenses/BSD-3-Clause
.. |BuildStatus| image:: https://travis-ci.org/open-license-manager/open-license-manager.svg?branch=develop
.. _BuildStatus: https://travis-ci.org/open-license-manager/open-license-manager
.. |CodacyBadge| image:: https://api.codacy.com/project/badge/Grade/62d6e1bb22d648bd85b6f3bc344a545a
.. _CodacyBadge: https://www.codacy.com/manual/gcontini/open-license-manager?utm_source=github.com&amp;utm_medium=referral&amp;utm_content=open-license-manager/open-license-manager&amp;utm_campaign=Badge_Grade
.. |codecov| image:: https://codecov.io/gh/open-license-manager/open-license-manager/branch/develop/graph/badge.svg
.. _codecov: https://codecov.io/gh/open-license-manager/open-license-manager
.. |issues| image:: https://img.shields.io/github/issues/open-license-manager/open-license-manager
.. _issues: http://github.com/open-license-manager/open-license-manager/issues
.. |forum| image:: https://img.shields.io/badge/forum-licensecc-blue.svg?style=flat
.. _forum: https://groups.google.com/d/forum/licensecc

Protect the software you develop from unauthorized copies, limit the usage in time, to a specific set of 
machines, or prevent the usage in  virtualized environments. It is an open source license management system that helps to keep your 
software closed |:smirk:| . Among the other features the most notable one is: if it runs on a "real hardware" 
it can generate a signature of that hardware and report if the signature doesn't match, because for instance 
the software has been copied to another pc.

A comprehensive :ref:`list of features <analysis/features:Features>`, and their status is available in the project wiki. 

If you're experiencing problems, or you just need informations you can't find here in the documentation,
please contact us on the `user forum <https://groups.google.com/forum/#!forum/licensecc>`_ (hosted on Google), we'll be happy to help. 

License (BSD)
**************
The project is donated to the community. It comes with a very large freedom of use for everyone, and it will always be. 
It uses a `BSD 3 clauses`_ licensing schema, that allows modification and inclusion in GPL and commercial software.

.. _BSD 3 clauses: https://opensource.org/licenses/BSD-3-Clause  

Project Structure
*******************
The software is made by 4 main sub-components:

* ``licensecc``    : the C++ library with a C api (the part you have to integrate in your software) with minimal (or no) external dependencies. This is the project you're currently looking at.
* ``lccinspector`` : a license debugger to be sent to the final customer to diagnose licensing problems or for calculating the hardware id before issuing the license.
* ``lccgen``       : a license generator (github project `lcc-license-generator`_ ) to initialize the library and generate the licenses.
* ``examples``     : usage samples (github project `examples <https://github.com/open-license-manager/examples>`_ ).

.. _lcc-license-generator: https://github.com/open-license-manager/lcc-license-generator

How to build
****************
Below an overview of the basic build procedure, provided as an example but if you really want to try we suggest you to refer to the detailed section
for your operating system: :ref:`Linux <development/Build-the-library:Build - Linux>` or :ref:`Windows <development/Build-the-library-windows:Build - Windows>`. 

Prerequisites
===================

* Operating system : Linux(Ubuntu, CentOS), Windows
* compilers        : GCC (Linux) MINGW (Linux cross compile for Windows), MINGW or MSVC (Windows) 
* tools            : Cmake(>3.6), git, make/ninja(linux)
* libraries        : If target is Linux Openssl is required. Windows depends only on system libraries. Boost is necessary to build license generator and to run the tests but it's NOT a dependency of the final `licensecc` library. 

For a complete list of dependencies and supported environments see the :ref:`dependencies <development/Dependencies:Dependencies>` section.
Clone the project. 

.. NOTE::
  It has submodules, don't forget the `--recursive` option.

.. code-block:: console

  git clone --recursive https://github.com/open-license-manager/open-license-manager.git
  cd open-license-manager/
  cd build

Build on Linux
===================

.. code-block:: console

  cmake .. -DCMAKE_INSTALL_PREFIX=../install
  make
  make install

Build on Windows (with MSVC 2017)
==================================

.. code-block:: console

  cmake .. -G "Visual Studio 16 2017 Win64" -DBOOST_ROOT="{Folder where boost is}" -DCMAKE_INSTALL_PREFIX=../install
  cmake --build . --target install --config Release

Cross compile with MINGW on Linux
=====================================

.. code-block:: console

  x86_64-w64-mingw32.static-cmake .. -DCMAKE_INSTALL_PREFIX=../install
  make
  make install

How to test
****************

On Linux:

.. code-block:: console

  make test

On Windows (MSVC):

.. code-block:: console

  ctest -C Release

How to use
**************
The `examples`_ repository shows various ways to integrate ``licensecc`` into your project.

.. _examples: https://github.com/open-license-manager/examples 

Branches and status
*********************

* On branch ``master`` there is the 'legacy' 1.0.0 version. This version is working but doesn't correspond to the current documentation, and we don't plan to actively fix it. There are well-known bugs and limitations. We still accept community contributions on this branch. Feel free to propose your pull request.   
* On branch ``develop`` there is the upcoming 2.0.0 version that corresponds to the documentation. This version is under development and has not been extensively used/tested. However we encourage users to download and use this one.   

How to contribute
********************

.. TIP::
  The easiest way you can solve your problems or ask help is through the `forums`_ (hosted on Google)

Otherwise you can open an issue in the `issue system`_. Have a look to the `contribution guidelines`_ before reporting.

We use `GitFlow`_ (or at least a subset of it). Remember to install the gitflow git plugin and use ``develop`` as default branch for your pull requests. 

.. _forums: https://groups.google.com/forum/#!forum/licensecc
.. _issue system: https://github.com/open-license-manager/open-license-manager/issues
.. _contribution guidelines: https://github.com/open-license-manager/open-license-manager/blob/develop/CONTRIBUTING.md
.. _GitFlow: https://datasift.github.io/gitflow/IntroducingGitFlow.html

* :ref:`genindex`
* :ref:`modindex`
* :ref:`search`

   
.. toctree::
   :glob:
   :maxdepth: 2
   :hidden:
   :caption: Build the library:
  
   development/*

.. toctree::
   :glob:
   :maxdepth: 2
   :hidden:
   :caption: Integrate and use:
  
   usage/*
   

.. toctree::
   :maxdepth: 2
   :hidden:
   :caption: API:
  
   api/public_api
   api/extend
      
.. toctree::
   :glob:
   :maxdepth: 2
   :hidden:
   :caption: Analysis:
  
   analysis/*

.. toctree::
   :glob:
   :maxdepth: 2
   :hidden:
   :caption: Miscellaneous:
  
   other/*
   
