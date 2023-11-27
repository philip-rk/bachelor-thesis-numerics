# bachelor-thesis-numerics

This repository serves to preserve the code I wrote in the course of my bachelor thesis on systems of Rydberg atoms.

In order to use it yourself there a two important classes that carry most of the functunality.
These are explained in detail in the following section.

## Lattice 
The lattice function is used to generate the set of basis states and the matrices of different terms.
It requires the number of lattice sites $L$ as an input. If no other arguments are provided it defaults
to a one dimensional chain-like lattice with with open boundary conditions in a constrained space with no neighbouring excitations.

### Additional parameters
These settings can be changed by providing additional parameters.
By setting legs=2, a two leg ladder geometry is used. Here $L$ corresponds to the number of sites in a single row, so the lattice
actually has $N=2L$ sites.
The boundary conditions can be changed by using either bc="OBC" or bc="PBC", for open and periodic boundary conditions respectively.
Lastly, everything can be generated in an unconstrained space by setting constraint=False.

### Outputs
The lattice class carries the following attributes.
self.sites simply gives the number of sites in a single row, $L$.
self.basis gives the full set of basis states, sorted by the number of excitations.

self.det, self.stag, self.rabi, self.hop and self.int are the give the matrices of the detuning, staggered-detuning, rabi, hopping and interaction term respectively.

## Matrix
The matrix class takes in a lattice object as the only required input.
This on its own isn't particularily useful yet, since it just results in an empty matrix with the appropiate dimensions,
so in addition the weight of the different terms of the Hamiltonian can be specified using lat, stag, rabi, hop and int for the
respective terms declared in the lattice.

The class then adds up the terms to form the complete Hamiltonian and calculates the ground state, which can be accessed using
self.gs for the ground state as well as self.energy and self.degen for the ground state energy and the degeneracy respectively.

