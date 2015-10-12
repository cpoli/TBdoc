:tocdepth: 2

Tight-Binding
==============================

.. toctree::
    :hidden:

    indexLatticeTB
    indexEigTB
    indexPlotTB
    indexPropagationTB

**TB** is a package providing a **Python** implementation of **Tight-Binding** models. It can be used to build up and solve tight-binding models with complex-valued onsite energies and hoppings. 

Main features of TB:

    * Written in fully vectorized **Numpy**.
    * Easy lattice shape selection.
    * Easy implementation of next neighbors hoppings, next next neighbors hoppings, etc..
    * Time evolution (linear and non-linear)
    * Easy implementation of magnetic field.
    * Easy implementation of strain.
    * Easy implementation of defects:

        * hopping disorder.
        * onsite disorder.
        * vacancy defects.
        * impurity defects (local change of hopping values).   
        * dimerization defects (change of hopping patterns).

   
Installation
----------------

**TB** is available at https://github.com/cpoli/python/TB

To use **TB**,  you need to install the programming language python and three additional packages:

    * python 3.x
    * numpy
    * scipy
    * matplotlib

See https://cpoli.github.io/python-doc.html for details.

Feedback
-----------------

Please send comments or suggestions for improvement to cpoli83 at hotmail dot fr