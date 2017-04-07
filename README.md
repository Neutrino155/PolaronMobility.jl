# PolaronMobility-FeynmanKadanoffOsakaHellwarth

These codes calculate the temperature-dependent polaron mobility for
a material. 

They solve Osaka's variational method for solving the Feynman model. 
For each temperature, the total free energy of the Feynman coupled
phonon-electron system is minimised by optimising coefficients which control
the spring-coupling coefficient and effective-mass for the phonon cloud. 

We then calculate the polaron mobility, with both the original low-temperature
FHIP approximation [Feynman1962], Kadanoff's [Kadanoff1964] (Boltzmann equation
motivated) phonon-emission correction to the FHIP, and Hellwarth's
[Hellwarth1999] method of returning to an earlier (non low-temperature) result
in Feynman1962, then directly calculating the contour integral for the polaron
self-energy with numerical integration.

Underlying all this is the simplified Frohlich Hamiltonian [Frohlich1952] for
a single electron interacting with a phonon cloud of non-interacting (harmonic)
phonons.
The electron-phonon interaction is particularly simple, just considering
a dipole interaction. 
This is folded into a dimensionless `alpha` parameter, practically constructed
from dielectric constants of a material, and a characteristic frequency of the
dielectric response. 
(In a simple covalent semiconductor system, this is the frequency of the
linear-optical mode, the only infrared active one.) 
The Feynman model is a beautiful solution of this most simple quantum field
problem where the quantum field variable of the phonon field is integrated out
by the path-integral approach to quantum mechanics, to leave an electron
interacting via a spring constant with an effective mass---a single particle
problem. 

These Julia codes use Hellwarth's [Hellwarth1999] presentation of Osaka's variational
free-energies for the Feynman model. 
We optimise the `v` and `w` parameters for these finite-temperature free energies. 
These can be alternatively restated the mass 'M' and spring-constant 'k' of the
coupled phonon-electron Feynman model. 

Here we apply these methods to the case of hybrid halide perovskites. 
The method provides the temperature dependent polaron-mobility without any free parameters. 
No arbitrary relaxation time is needed or used. The scattering processes are
treated directly, by including an effective electron-phonon coupling in the
specification of the Frohlich 'alpha' parameter, and then all other features
come from solving the model. 
The original Feynman model is correct to all orders in alpha, and the Hellwarth
direct contour-integration of the general Feynman mobility statement is
suitable for high temperature.

It was necessary to return to these (rather old!) papers and resolve the
models, as hybrid halide perovskites are soft materials with low energy
phonons. Therefore the effective temperature in terms of a reduced
thermodynamic beta (Beta=hbar omega / (k_Boltzmann * Temperature) ) is much
smaller than previously considered. 

A finaly note that in [Hellwarth1999], there is a mistake in the formula for 'b',
which is also present in their prior PRL [Biaggio1997]. 
It is correct in [Feynman1962], where there is no factor of b on the right-hand
side. 
It doesn't matter too much, as setting it to zero makes ~0.1% difference in the
eventual mobility. 
However, since we're integrating numerically anyway, we may as well calculate
it explicitly.

## Bibliography

A bibliography in vague order of utility; read the first ones first!

Feynman also describes his Polaron solution in more detail in both 'Statistical
Mechanics' (Feynman1972) and 'Quantum Mechanics and Path Integrals'
(FeynmanHibbs1965). Note that the differing presentations of Feynman do not agree perfectly!

J.T. Devreese's "Fröhlich Polarons. Lecture course including detailed
theoretical derivations" notes on the ArXiv is a very good place to start with general introductions.
https://arxiv.org/abs/1611.06122


```

@article{Hellwarth1999,
  doi = {10.1103/physrevb.60.299},
  url = {https://doi.org/10.1103%2Fphysrevb.60.299},
  year  = {1999},
  month = {jul},
  publisher = {American Physical Society ({APS})},
  volume = {60},
  number = {1},
  pages = {299--307},
  author = {Robert W. Hellwarth and Ivan Biaggio},
  title = {Mobility of an electron in a multimode polar lattice},
  journal = {Physical Review B}
}

@article{Kadanoff1963,
  doi = {10.1103/physrev.130.1364},
  url = {https://doi.org/10.1103%2Fphysrev.130.1364},
  year  = {1963},
  month = {may},
  publisher = {American Physical Society ({APS})},
  volume = {130},
  number = {4},
  pages = {1364--1369},
  author = {Leo P. Kadanoff},
  title = {Boltzmann Equation for Polarons},
  journal = {Physical Review}
}

@article{Feynman1962,
  doi = {10.1103/physrev.127.1004},
  url = {https://doi.org/10.1103%2Fphysrev.127.1004},
  year  = {1962},
  month = {aug},
  publisher = {American Physical Society ({APS})},
  volume = {127},
  number = {4},
  pages = {1004--1017},
  author = {R. P. Feynman and R. W. Hellwarth and C. K. Iddings and P. M. Platzman},
  title = {Mobility of Slow Electrons in a Polar Crystal},
  journal = {Physical Review}
}


@article{Feynman1955,
  doi = {10.1103/physrev.97.660},
  url = {https://doi.org/10.1103%2Fphysrev.97.660},
  year  = {1955},
  month = {feb},
  publisher = {American Physical Society ({APS})},
  volume = {97},
  number = {3},
  pages = {660--665},
  author = {R. P. Feynman},
  title = {Slow Electrons in a Polar Crystal},
  journal = {Physical Review}
}

@article{Schultz1959,
  doi = {10.1103/physrev.116.526},
  url = {https://doi.org/10.1103%2Fphysrev.116.526},
  year  = {1959},
  month = {nov},
  publisher = {American Physical Society ({APS})},
  volume = {116},
  number = {3},
  pages = {526--543},
  author = {T. D. Schultz},
  title = {Slow Electrons in Polar Crystals: Self-Energy,  Mass,  and Mobility},
  journal = {Physical Review}
}

@article{Osaka1961,
  doi = {10.1143/ptp.25.517},
  url = {https://doi.org/10.1143%2Fptp.25.517},
  year  = {1961},
  month = {apr},
  publisher = {Oxford University Press ({OUP})},
  volume = {25},
  number = {4},
  pages = {517--536},
  author = {Yukio \=Osaka},
  title = {Theory of Polaron Mobility},
  journal = {Progress of Theoretical Physics}
}

@article{Frohlich1952,
  doi = {10.1098/rspa.1952.0212},
  url = {https://doi.org/10.1098%2Frspa.1952.0212},
  year  = {1952},
  month = {dec},
  publisher = {The Royal Society},
  volume = {215},
  number = {1122},
  pages = {291--298},
  author = {H. Frohlich},
  title = {Interaction of Electrons with Lattice Vibrations},
  journal = {Proceedings of the Royal Society A: Mathematical,  Physical and Engineering Sciences}
}

@article{Thornber1970,
  doi = {10.1103/physrevb.1.4099},
  url = {https://doi.org/10.1103%2Fphysrevb.1.4099},
  year  = {1970},
  month = {may},
  publisher = {American Physical Society ({APS})},
  volume = {1},
  number = {10},
  pages = {4099--4114},
  author = {K. K. Thornber and Richard P. Feynman},
  title = {Velocity Acquired by an Electron in a Finite Electric Field in a Polar Crystal},
  journal = {Physical Review B}
}

```