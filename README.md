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
for their own systems and use cases. The user assumes all risks associated with
compiling, running, modifying, or relying on this development version.
