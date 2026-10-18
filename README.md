# PARSEC 1.5 FDET-AFM Implemented Version

Modified by Dingxin Fan.

This repository provides a full packaged copy of the PARSEC 1.5 source tree
with FDET-based AFM simulation support implemented.

## Package

- `parsec1.5_DF.tar.gz`

The package contains the full `parsec_1.5` directory used for this development
version, including the added FDET/AFM documentation file:

- `parsec_1.5/README_FDET_AFM_DF.md`

## Added Functionality

This version adds support for FDET-based AFM simulation workflows, including:

- External frozen-sample `pot.dat` field reading.
- AFM/FDET `pot.dat` output.
- Non-additive kinetic-energy and kinetic-potential terms.
- FDET input keywords and data structures.
- FDET corrections in SCF potential updates, Hartree/XC handling, total energy,
  and force calculations.
- Slab-periodic FDET support with external point charges.
- Stampede3-oriented build configuration updates.

## Update 2026-10-18

The package now matches the source archive on https://parsecdev.vercel.app/code.html
(release of 2026-10-18). Changes since the first upload:

- FDET fixes: the sample point charges are no longer added to the electronic
  ionic potential (the sample ions already act through `pot.dat`), and the
  non-additive kinetic energy is summed over processors and scaled by h^3.
- Warm start for AFM scans: when the tip moves by whole grid steps between
  `minimization manual` steps, the converged density, orbitals and Hartree
  potential are translated with it (about 3x fewer SCF steps per scan point).
- New keywords `hartree_cg_tolerance` and `hartree_cg_criterion` for the CG
  Poisson solver (defaults unchanged).
- Stability updates from July 2026, gfortran portability fixes and a Windows
  (MSYS2 UCRT64) build configuration.
- The old prebuilt Stampede3 binary was removed. Build from source.

Details and input recommendations for FDET-AFM runs are in
`parsec_1.5/README_FDET_AFM_DF.md`.

## Usage

To unpack:

```bash
tar -xzf parsec1.5_DF.tar.gz
cd parsec_1.5/src
```

On Stampede3, use the Stampede3 configuration under:

```text
parsec_1.5/src/build/config/make.stampede3_skx_intel
```

## Status

Preliminary tests have passed for this migrated PARSEC 1.5 FDET-based AFM code.
However, this version is still under development. Users should validate the code
for their own systems and use cases. Users use it at their own risk.
