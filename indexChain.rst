

Tight-Binding Chain
========================

.. toctree::
    :hidden:

    chainTB
    examplesChain1
    examplesChain2

Motivations
-------------------

**chainTB** package models a one-dimensional tight-binding dimer chain with real and/or complex valued hoppings and onsite energies. Defects in the dimer chain can be introduced by locally modifying the on-site energies and/or the hoppings or, by changing the dimerization pattern i.e. switching intradimer with interdimer hopping. The package can reproduce Shockley [Sho39]_ and SSH [Su79]_ states. Note that these systems  acquired recently a renewed interest considering complex onsites energies allowing to amplify the topologically protected midgap state [Sch13]_,  [Pol15]_.

This package can then by useful to illustrate the concepts of:

    * Parity-Time symmetry and and Parity-Time symmetry breaking.

    * Sublattice symmetry breaking (for an odd number of sites), resulting in a mode of zero energy.

    * Localized states introduced by dimerization defects in the dimerization pattern.

    * Topologically protected states:

        * Localized in one edge of dimer chain with alternating couplings and sublattice symmetry breaking, the Shokley state.

        * Localized at the dimerization defect in a dimer chain with with alternating couplings and sublattice symmetry breaking, the so-called SSH model.


The chain is defined by:

* a unit cell composed of two sites labeled A (blue) and B (red):

.. image:: ../TBfig/chain_n2/cell.png
    :width:  50%
    :align: center

.. note::

    The chain starts with a A site.

* two hoppings (with non zeros real parts), the intradimer coupling :math:`t_{ab}=t_a` which links the A sites to the B sites, and the interdimer hopping :math:`t_{ba} =t_b` which links the B sites to the A sites.

* two onsite energies :math:`\epsilon_{a}` for the A sites, and :math:`\epsilon_{b}` for the B sites.

* For an even number of sites :math:`n=2m` the chain is composed of :math:`m` unit cells.

    For :math:`n=10`:

    .. image:: ../TBfig/chain_n10/chain_even.png
        :height: 100px
        :width:  95%
        :align: center


* For an odd number of sites :math:`2n+1` the chain is composed of :math:`n` unit cells plus an extra A site.

    For :math:`n=11`:

    .. image:: ../TBfig/chain_n11/chain_odd.png
        :height: 100px
        :width:  95%
        :align: center

The defects implemented:

    * change locally the onsite energies

    * change locally the hoppings

    * introduce a defect in the dimerization pattern

    * hopping disorder

    * onsite energy disorder

**chainTB** can:

    * obtain the spectrum (eigenenergies of the tight-binding Hamiltonian) and the probability densities of the states of the system (absolute value squared eigenvectors of the Hamiltonian).

    * obtain sublattice polarization (sum of the probability densities of one sublattice).

    * select polarized states  (revealing zero modes).

    * test robustness to disorder by implementing hopping disorder.

    * get the time evolution of the field (using the Crank-Nicolson method).

    * get the time evolution of the field with adiabatic pumping (smooth variation of the hoppings).


References
--------------------------------------


.. [Sho39] W. Shockley, *On the surface states associated with a periodic potential*.
    Phys. Rev. **56**, 317 (1939)

.. [Su79] W.P. Su, J.R. Schrieffer, and A.J. Heeger, *Solitons in conducting polymers*.
    Phys. Rev. Lett. **42**, 1698 (1979).

.. [Sch13] Schomerus, H. *Topologically protected midgap states in complex photonic lattices*.
    Opt. Lett. **38**, 1912–1914 (2013).

.. [Pol15] C. Poli, M. Bellec, U.Kuhl, F. Mortessagne, and H. Schomerus, *Selective enhancement of topologically induced interface states in a dielectric resonator chain*.
    Nat. Commun. **6** 6710, (2015).


Feedback
-----------------

Please send comments or suggestions for improvement to cpoli83 at hotmail dot fr