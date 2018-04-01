# PolaronMobility.jl

[![Build Status](https://travis-ci.org/jarvist/PolaronMobility.jl.svg?branch=master)](https://travis-ci.org/jarvist/PolaronMobility.jl)
[![Coverage Status](https://coveralls.io/repos/jarvist/PolaronMobility.jl/badge.svg?branch=master&service=github)](https://coveralls.io/github/jarvist/PolaronMobility.jl?branch=master)
[![codecov.io](http://codecov.io/github/jarvist/PolaronMobility.jl/coverage.svg?branch=master)](http://codecov.io/github/jarvist/PolaronMobility.jl?branch=master)

These codes calculate the temperature-dependent polaron mobility for
a material. 
This is based on the Feynman variational solution to the Polaron problem. 
The electron-phonon coupling is treated as an effective α (alpha) Frohlich
Hamiltonian parameter. 
The band structure is treated with an effective mass theory. 
The variational problem is solved numerically for finite-temperature free
energies, rather than by the asymptotic solutions to the athermal energies, as
often found in the textbooks.  
The mobility is calculated numerically by integrating the polaron self-energy
along the imaginary axis, as well as with the Kadanoff Boltzmann equation
approximation, and the FHIP low-temperature asymptotic solution. 

We provided parameters for various metal-halide Perovskites, and other
interesting systems.

The motivation for developing these codes was to enable polaron mobility
calculations on arbitrary materials. 
They also provide the only extant implementation of Feynman's variational
method.  
They offer a convenient basis for writing codes that build on these variational
solutions. 

More extensive documentation is available
[![here](https://img.shields.io/badge/docs-latest-blue.svg)](https://jarvist.github.io/PolaronMobility.jl/),
which is perhaps easiest to read and understand alongside the first paper:
[ArXiv:1704.05404](https://arxiv.org/abs/1704.05404)
/ [Frost2017PRB](https://doi.org/10.1103/PhysRevB.96.195202).

The model inputs are the dielectric constants (ϵ-static and ϵ-optic),
a characteristic phonon frequency (ω), and the bare-electron band
effective-mass (me).  
These values can be relatively easily calculated in the
ab-initio electronic structure package of your choosing, or measured directly. 

From these four values, the code solves a temperature-dependent polaron model. 
This is done by variationally optimising the temperature-dependent
free-energies for the coupled electron-phonon system. 
These optimised parameters describe the polaron with the infinite quantum field
of lattice vibrations 'integrated through', and replaced with a phonon-drag
term. 
From this the polaron features such as effective-mass, size of the
wavefunction, frequency of energy oscillation etc. can be calculated. 

This polaron state can then be used as an input to further models for polaron
mobility. 

The codes are designed to produce a set of temperature-dependent mobilities and
other data, for direct incorporation into a scientific publication. 

May your phonons drag in a manner truly sublime.

![MAPI Polaron mobility, plotted vs experimental data](mobility-calculated-experimental.png)

## Installation

These codes require Julia >0.6 . They are structured as a full Julia package, but are not yet registered with the central METADATA package repository. 

To install, type the following at the Julia REPL:

```
julia> Pkg.clone("git://github.com/Jarvist/PolaronMobility.jl.git")
```

## Research outputs

As an example, here are some indicative figures from an early version of the codes. 
These are specified for transport in hybrid lead iodide perovskite. 

Polaron mobilities, three different ways
![Polaron mobilities, three different ways](mobility-calculated.png)

Effective mass of phonon cloud
![Effective mass of phonon cloud](mass.png)

Spring constant for coupling to phonon cloud
![Spring constant for coupling to phonon cloud](spring.png)

Variational (temperature-dependent free-energy) parameters for the coupled system
![Variational (temperature-dependent free-energy) parameters for the coupled system](variational.png)


## Community guidelines

Contributions to the code (extending that which is calculated), or additional
physical systems / examples, are very welcome. 

If you have questions about the software, scientific questions, or find errors,
please create a [GitHub issue](https://github.com/jarvist/PolaronMobility.jl/issues). 

If you find this package (or snippets, such as the entered and tested
free-energy expressions) useful for your work, please cite the paper 
[Frost2017PRB](https://doi.org/10.1103/PhysRevB.96.195202). 

```
@article{Frost2017,
  doi = {10.1103/physrevb.96.195202},
  url = {https://doi.org/10.1103/physrevb.96.195202},
  year  = {2017},
  month = {nov},
  publisher = {American Physical Society ({APS})},
  volume = {96},
  number = {19},
  author = {Jarvist Moore Frost},
  title = {Calculating polaron mobility in halide perovskites},
  journal = {Physical Review B}
}
```

