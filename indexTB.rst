.. TB documentation master file, created by
   sphinx-quickstart on Fri Oct  2 15:46:25 2015.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

Tight-Binding
==============================


**TB** is a package providing a Python implementation of tight-binding models. It can be used to build up and solve tight-binding models with complex valued onsite energies and/or hoppings. 

Main features of TB:

    * Written in fully vectorized **numpy**.
    * Easy lattice shape implementation.
    * Easy implementation of next neighbors hoppings, next next neighbors hoppings, etc..
    * Time evolution (linear and non-linear)
    * Easy implementation of magnetic field.
    * Easy implementation of strain.
    * Easy implementation of defects:

        * hopping disorder
        * vacancy defects
        * impurity defects (local change of hopping values).   
        * dimerization defects (change of hopping patterns).


.. toctree::
    :titlesonly:

    latticeTB
    eigTB
    plotTB
    propagationTB
    indexChain

   
Installation
----------------

**TB** is available at https://github.com/cpoli/python/TB

To use **TB**,  you need to install the programming language python and three additional packages:

    * python 3.x
    * numpy
    * scipy
    * matplotlib
