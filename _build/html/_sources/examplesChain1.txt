
PT-symmetry
======================================



These examples illustrate the PT-symmetry and the PT-symmetry breaking.

.. note::
    Throughout the examples, the hoppings :math:`t_{ab}=t_a` and :math:`t_{ba}=t_b` are real and the onsite energies are purely imaginary with :math:`\epsilon_a=i\gamma` and :math:`\epsilon_b=-i\gamma`. Then, the A sites are amplified (positive imaginary part) and the B sites are absorbed (negative imaginary part).


Dimer
--------------

.. image:: ../TBfig/chain_n2/lattice_t(1+0j).png
    :height: 80px
    :width:  100%
    :align: center

The Hamiltian reads

.. math::

    \left( \begin{array}{cc}
    i\gamma & t \\
    t & i\gamma \end{array} \right)

Hermitian case
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
In the case :math:`\gamma=0`, the Hamiltonian is real symmetric, the eigenenergies are real and given by: :math:`E_\pm=\pm t`.

.. code-block:: python

    from chainTB import *
    # lattice
    tags = [b'a', b'b']
    ri = [[0, 0], [1, 0]]
    pv = [[2, 0], [2, 0]]
    n = 2
    ta = 1.
    chain_tb = latticeTB(tags=tags, ri=ri, pv=pv)
    chain_tb.get_lattice(nx=2, ny=1)
    # solve eigenvalue problem
    eig_chain = eigChain(lat=chain_tb)
    eig_chain.set_hop(ta=ta)
    eig_chain.get_ham()
    eig_chain.get_eig()
    # plots
    plot_chain = plotTB(sys=eig_chain)
    lattice  = plot_chain.plt_lattice(plt_label=True, ms=50, fs=20)
    fig_spec = plot_chain.plt_spec(ms=20, pola_tag=b'a')
    #propagation
    prop_chain = propagationTB(coor=eig_chain.coor, steps=1400, dz=0.02)
    psi_init =  [1, 0]
    prop_chain.get_prop(ham=eig_chain.ham, psi_init=psi_init, norm=True)
    fig_prop = prop_chain.plt_prop1d()
    fig_prop_dimer = prop_chain.plt_prop_dimer()
    # save figures
    save_chain = saveFigTB(sys=eig_chain, hop_tags=['t'], hop=[ta], dir_name='chain', ext='png')
    save_chain.save_fig(fig_spec, 'spec')
    save_chain.save_fig(fig_prop_dimer, 'prop_dimer')
    save_chain.save_fig(fig_prop, 'prop')

.. image:: ../TBfig/chain_n2/spec_t(1+0j)_ea0,8j_eb-0,8j.png
    :width: 55%
    :align: center

.. image:: ../TBfig/chain_n2/prop_dimer_t(1+0j)_ea0,8j_eb-0,8j.png
    :width: 45%

.. image:: ../TBfig/chain_n2/prop_t(1+0j)_ea0,8j_eb-0,8j.png
    :width: 45%



Non-Hermitian case
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

In the case :math:`\gamma\neq0`, the Hamiltonian is complex non-Hermitian, 
and display the space-time reflection symmetry. The eigenenergies are given by: :math:`E_\pm=\pm \sqrt{t^2-|\gamma|^2}`. As the result, the energies are real if :math:`t>\gamma`, degenerated if :math:`t=\gamma` (PT-symmetric phase), and complex if :math:`t<\gamma`. :math:`\gamma` (broken PT-symmetry). :math:`t=\gamma`. :math:`\gamma` is the PT-symmetry breaking point.

.. note::

    This example shows that a non-Hermitian matrix can have a real spectrum.


PT-symmetry
"""""""""""""""""""

Below the PT-symmetry breaking point, the eigenenergies are real: :math:`E_\pm=\pm \sqrt{t^2-|\gamma|^2}`.

.. code-block:: python

    from chainTB import *
    # lattice
    tags = [b'a', b'b']
    ri = [[0, 0], [1, 0]]
    pv = [[2, 0], [2, 0]]
    n = 2
    ta = 1.
    on = [0.8j, -0.8j]
    chain_tb = latticeTB(tags=tags, ri=ri, pv=pv)
    chain_tb.get_lattice(nx=2, ny=1)
    fig_latttice = chain_tb.plt_lattice(plt_label=True, ms=50, fs=20)
    # solve eigenvalue problem
    eig_chain = eigChain(lat=chain_tb)
    eig_chain.set_onsite(on=on)
    eig_chain.set_hop(ta=ta)
    eig_chain.get_ham()
    eig_chain.get_eig()
    # plots
    plot_chain = plotTB(sys=eig_chain)
    fig_spec = plot_chain.plt_spec(ms=20, pola_tag=b'a')
    #propagation
    prop_chain = propagationTB(coor=eig_chain.coor, steps=1400, dz=0.02)
    psi_init =  [1, 0]
    prop_chain.get_prop(ham=eig_chain.ham, psi_init=psi_init, norm=True)
    fig_prop = prop_chain.plt_prop1d()
    fig_prop_dimer = prop_chain.plt_prop_dimer()
    # save figures
    save_chain = saveFigTB(sys=eig_chain, hop_tags=['t'], hop=[ta], dir_name='chain', ext='png')
    save_chain.save_fig(fig_latttice, 'lattice')
    save_chain.save_fig(fig_spec, 'spec')
    save_chain.save_fig(fig_prop_dimer, 'prop_dimer')
    save_chain.save_fig(fig_prop, 'prop')

.. image:: ../TBfig/chain_n2/spec_t(1+0j)_ea0,8j_eb-0,8j.png
    :width: 55%
    :align: center

.. image:: ../TBfig/chain_n2/prop_dimer_t(1+0j)_ea0,8j_eb-0,8j.png
    :width: 45%

.. image:: ../TBfig/chain_n2/prop_t(1+0j)_ea0,8j_eb-0,8j.png
    :width: 45%


breaking point
"""""""""""""""""""

At the breaking point, :math:`\gamma=t`, the eigenenergies coincide: :math:`E_\pm=0`.

.. code-block:: python

    from chainTB import *
    # lattice
    tags = [b'a', b'b']
    ri = [[0, 0], [1, 0]]
    pv = [[2, 0], [2, 0]]
    n = 2
    ta = 1.
    on = [1j, -1j]
    chain_tb = latticeTB(tags=tags, ri=ri, pv=pv)
    chain_tb.get_lattice(nx=2, ny=1)
    chain_tb.plt_lattice(plt_label=True, ms=50, fs=20)
    # solve eigenvalue problem
    eig_chain = eigChain(lat=chain_tb)
    eig_chain.set_onsite(on=on)
    eig_chain.set_hop(ta=ta)
    eig_chain.get_ham()
    eig_chain.get_eig()
    # plots
    plot_chain = plotTB(sys=eig_chain)
    fig_spec = plot_chain.plt_spec(ms=20, pola_tag=b'a')
    #propagation
    prop_chain = propagationTB(coor=eig_chain.coor, steps=1400, dz=0.02)
    psi_init =  [1, 0]
    prop_chain.get_prop(ham=eig_chain.ham, psi_init=psi_init, norm=True)
    fig_prop = prop_chain.plt_prop1d()
    fig_prop_dimer = prop_chain.plt_prop_dimer()
    # save figures
    save_chain = saveFigTB(sys=eig_chain, hop_tags=['t'], hop=[ta], dir_name='chain', ext='png')
    save_chain.save_fig(fig_spec, 'spec')
    save_chain.save_fig(fig_prop_dimer, 'prop_dimer')
    save_chain.save_fig(fig_prop, 'prop')

.. image:: ../TBfig/chain_n2/spec_t(1+0j)_ea1j_eb-1j.png
    :width: 55%
    :align: center

.. image:: ../TBfig/chain_n2/prop_dimer_t(1+0j)_ea1j_eb-1j.png
    :width: 45%

.. image:: ../TBfig/chain_n2/prop_t(1+0j)_ea1j_eb-1j.png
    :width: 45%


broken PT-symmetry
""""""""""""""""""""""""""""""""""""""

Above the PT-symmetry breaking point, :math:`\gamma>t`, the eigenenergies are complex: :math:`E_\pm= \pm i \sqrt{\gamma^2-t^2}`.



.. code-block:: python

    from chainTB import *
    # lattice
    tags = [b'a', b'b']
    ri = [[0, 0], [1, 0]]
    pv = [[2, 0], [2, 0]]
    n = 2
    ta = 1.
    on = [1.2j, -1.2j]
    chain_tb = latticeTB(tags=tags, ri=ri, pv=pv)
    chain_tb.get_lattice(nx=n, ny=1)
    chain_tb.plt_lattice(plt_label=True, ms=50, fs=20)
    # solve eigenvalue problem
    eig_chain = eigChain(lat=chain_tb)
    eig_chain.set_onsite(on=on)
    eig_chain.set_hop(ta=ta)
    eig_chain.get_ham()
    eig_chain.get_eig()
    # plots
    plot_chain = plotTB(sys=eig_chain)
    fig_spec = plot_chain.plt_spec(ms=20, pola_tag=b'a')
    #propagation
    prop_chain = propagationTB(coor=eig_chain.coor, steps=1400, dz=0.01)
    psi_init =  [1, 0]
    prop_chain.get_prop(ham=eig_chain.ham, psi_init=psi_init, norm=True)
    fig_prop_0 = prop_chain.plt_prop1d()
    fig_prop_dimer_0 = prop_chain.plt_prop_dimer()
    psi_init =  [0, 1]
    prop_chain.get_prop(ham=eig_chain.ham, psi_init=psi_init, norm=True)
    fig_prop_1 = prop_chain.plt_prop1d()
    fig_prop_dimer_1 = prop_chain.plt_prop_dimer()
    # save figures
    save_chain = saveFigTB(sys=eig_chain, hop_tags=['t'], hop=[ta], dir_name='chain', ext='png')
    save_chain.save_fig(fig_spec, 'spec')
    save_chain.save_fig(fig_prop_dimer_0, 'prop_dimer_0')
    save_chain.save_fig(fig_prop_dimer_1, 'prop_dimer_1')
    save_chain.save_fig(fig_prop_0, 'prop_0')
    save_chain.save_fig(fig_prop_1, 'prop_1')


.. image:: ../TBfig/chain_n2/spec_t(1+0j)_ea1,2j_eb-1,2j.png
    :width: 55%
    :align: center

.. image:: ../TBfig/chain_n2/prop_dimer_0_t(1+0j)_ea1,2j_eb-1,2j.png
    :width: 45%

.. image:: ../TBfig/chain_n2/prop_dimer_1_t(1+0j)_ea1,2j_eb-1,2j.png
    :width: 45%

.. image:: ../TBfig/chain_n2/prop_0_t(1+0j)_ea1,2j_eb-1,2j.png
    :width: 45%

.. image:: ../TBfig/chain_n2/prop_1_t(1+0j)_ea1,2j_eb-1,2j.png
    :width: 45%

Dimer chain
----------------------------


The chain is composed of :math:`n` dimers *i.e.* :math:`n` sites A and :math:`n` sites B. The chain starts with a A site and ends with a B site.

.. image::  ../TBfig/chain_n20/lattice_t(1+0j).png
    :height: 80px
    :width:  100%
    :align: center

Hermitian case
^^^^^^^^^^^^^^^

.. code-block:: python

    # lattice
    tags = [b'a', b'b']
    ri = [[0, 0], [1, 0]]
    pv = [[2, 0], [2, 0]]
    n = 20
    ta = 1.
    chain_tb = latticeTB(tags=tags, ri=ri, pv=pv)
    chain_tb.get_lattice(nx=n, ny=1)
    fig_lattice = chain_tb.plt_lattice(plt_label=True, ms=15, fs=20, figsize=(10, 2.8))
    # solve eigenvalue problem
    eig_chain = eigChain(lat=chain_tb)
    eig_chain.set_hop(ta=ta)
    eig_chain.get_ham()
    eig_chain.get_eig()
    # plots
    plot_chain = plotTB(sys=eig_chain)
    fig_spec = plot_chain.plt_spec(ms=20, pola_tag=b'a')
    #propagation
    prop_chain = propagationTB(coor=eig_chain.coor, steps=1400, dz=0.05)
    psi_init =  np.ones(eig_chain.sites) / np.sqrt(eig_chain.sites)
    prop_chain.get_prop(ham=eig_chain.ham, psi_init=psi_init, norm=True)
    fig_prop = prop_chain.plt_prop1d()
    # save figures
    save_chain = saveFigTB(sys=eig_chain, hop_tags=['t'], hop=[ta], dir_name='chain', ext='png')
    save_chain.save_fig(fig_lattice, 'lattice')
    save_chain.save_fig(fig_spec, 'spec')
    save_chain.save_fig(fig_prop, 'prop')

.. image:: ../TBfig/chain_n20/spec_t(1+0j)_ea0j_eb0j.png
    :width: 45%

.. image:: ../TBfig/chain_n20/prop_t(1+0j)_ea0j_eb0j.png
    :width: 45%

Non-Hermitian case
^^^^^^^^^^^^^^^^^^^^^

PT-symmetry
"""""""""""""""""""""""""""""""

.. code-block:: python

    from chainTB import *

    # lattice
    tags = [b'a', b'b']
    ri = [[0, 0], [1, 0]]
    pv = [[2, 0], [2, 0]]
    n = 20
    ta = 1.
    on = [0.1j, -0.1j]
    chain_tb = latticeTB(tags=tags, ri=ri, pv=pv)
    chain_tb.get_lattice(nx=n, ny=1)
    chain_tb.plt_lattice(plt_label=True, ms=15, fs=20)
    # solve eigenvalue problem
    eig_chain = eigChain(lat=chain_tb)
    eig_chain.set_onsite(on=on)
    eig_chain.set_hop(ta=ta)
    eig_chain.get_ham()
    eig_chain.get_eig()
    # plots
    plot_chain = plotTB(sys=eig_chain)
    fig_spec = plot_chain.plt_spec(ms=20, pola_tag=b'a')
    #propagation
    prop_chain = propagationTB(coor=eig_chain.coor, steps=1400, dz=0.05)
    psi_init =  np.ones(eig_chain.sites) / np.sqrt(eig_chain.sites)
    prop_chain.get_prop(ham=eig_chain.ham, psi_init=psi_init, norm=True)
    fig_prop = prop_chain.plt_prop1d()
    # save figures
    save_chain = saveFigTB(sys=eig_chain, hop_tags=['t'], hop=[ta], dir_name='chain', ext='png')
    save_chain.save_fig(fig_spec, 'spec')
    save_chain.save_fig(fig_prop, 'prop')

.. image:: ../TBfig/chain_n20/spec_t(1+0j)_ea0,1j_eb-0,1j.png
    :width: 45%

.. image:: ../TBfig/chain_n20/prop_t(1+0j)_ea0,1j_eb-0,1j.png
    :width: 45%


broken PT-symmetry
"""""""""""""""""""""""""""""""
.. code-block:: python

    from chainTB import *
    tags = [b'a', b'b']
    ri = [[0, 0], [1, 0]]
    pv = [[2, 0], [2, 0]]
    n = 20
    ta = 1.
    on = [0.2j, -0.2j]
    chain_tb = latticeTB(tags=tags, ri=ri, pv=pv)
    chain_tb.get_lattice(nx=n, ny=1)
    chain_tb.plt_lattice(plt_label=True, ms=15, fs=20)
    # solve eigenvalue problem
    eig_chain = eigChain(lat=chain_tb)
    eig_chain.set_onsite(on=on)
    eig_chain.set_hop(ta=ta)
    eig_chain.get_ham()
    eig_chain.get_eig()
    state_a = eig_chain.get_state_pola(b'a')
    state_b = eig_chain.get_state_pola(b'b')
    # plots
    plot_chain = plotTB(sys=eig_chain)
    fig_spec = plot_chain.plt_spec(ms=20, pola_tag=b'a')
    fig_state_a = plot_chain.plt_intensity1d(state_a, ms=20)
    fig_state_b = plot_chain.plt_intensity1d(state_b, ms=20)
    #propagation
    prop_chain = propagationTB(coor=eig_chain.coor, steps=1400, dz=0.05)
    psi_init =  np.ones(eig_chain.sites) / np.sqrt(eig_chain.sites)
    prop_chain.get_prop(ham=eig_chain.ham, psi_init=psi_init, norm=True)
    fig_prop = prop_chain.plt_prop1d()
    # save figures
    save_chain = saveFigTB(sys=eig_chain, hop_tags=['t'], hop=[ta], dir_name='chain', ext='png')
    save_chain.save_fig(fig_spec, 'spec')
    save_chain.save_fig(fig_state_a, 'state_a')
    save_chain.save_fig(fig_state_b, 'state_b')
    save_chain.save_fig(fig_prop, 'prop')

.. image:: ../TBfig/chain_n20/spec_t(1+0j)_ea0,2j_eb-0,2j.png
    :width: 55%
    :align: center

.. image:: ../TBfig/chain_n20/state_a_t(1+0j)_ea0,2j_eb-0,2j.png
    :width: 45%

.. image:: ../TBfig/chain_n20/state_b_t(1+0j)_ea0,2j_eb-0,2j.png
    :width: 45%

.. image:: ../TBfig/chain_n20/prop_t(1+0j)_ea0,2j_eb-0,2j.png
    :width: 65%
    :align: center

The state with  :math:`\langle A|A \rangle>1/2` is amplified.

