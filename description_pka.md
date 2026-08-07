# Radiation damage from a primary knock-on atom

## The question

How much kinetic energy must be given to one lattice atom before the crystal fails to recover completely?

In radiation-damage simulations, an energetic neutron, ion, or recoil can transfer energy to a lattice atom. That atom becomes a **primary knock-on atom (PKA)** and transfers energy to its neighbors through collisions.

This Atomify activity uses a deliberately small UO2 cell and low PKA energies so that the calculation can run in a web browser. It is a **teaching model**, not a research-quality prediction of displacement threshold energy.

## Your controls

At the top of `PKA_O.in`, change only:

- `EPKA`: recoil kinetic energy in eV
- `DX`, `DY`, `DZ`: recoil direction
- optionally `DCUT`: displacement threshold in Angstrom

Start with oxygen PKAs at 10, 25, 50, 75, and 100 eV. Compare directions [100], [110], and [111].

## Watch four signals

1. **MSD**: mean-square displacement of the whole crystal.
2. **Displaced atom count**: atoms farther than `DCUT` from their pre-PKA reference positions.
3. **Maximum displacement**: the largest individual atomic displacement.
4. **PKA kinetic energy**: how quickly the recoil energy leaves the original atom.

The important distinction is between **peak damage** and **residual damage**. Many atoms may move during the ballistic event while very few remain displaced after the lattice relaxes.

## Suggested investigation

For each direction, increase `EPKA` until a run finishes with one or more residual displaced atoms. Repeat near that transition with smaller energy increments. Report an *apparent* directional displacement threshold for this model.

Then run `PKA_U.in` and compare an oxygen recoil with a uranium recoil. Explain the result using mass, momentum transfer, lattice geometry, and the limitations of the potential.

## Scientific caveat

The supplied AnO2 interaction was designed for ordinary interatomic separations. Radiation cascades can drive atoms to extremely short separations, where radiation-damage simulations normally require a short-range screened nuclear repulsion such as ZBL. Therefore this exercise should remain in the low-energy, qualitative regime unless the potential is augmented and validated for collision physics.
