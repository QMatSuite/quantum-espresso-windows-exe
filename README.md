# Quantum ESPRESSO for Windows

[![Build (GitHub Actions)](https://github.com/QMatSuite/quantum-espresso-windows-exe/actions/workflows/import-from-toolchain.yml/badge.svg)](https://github.com/QMatSuite/quantum-espresso-windows-exe/actions/workflows/import-from-toolchain.yml)
![Signing (Microsoft Trusted Signing)](https://img.shields.io/badge/Signing-Microsoft%20Trusted%20Signing-2F81F7)
[![Attestation (GitHub Artifact Attestation)](https://img.shields.io/badge/Attestation-GitHub%20Artifact%20Attestation-2DA44E)](https://github.com/QMatSuite/quantum-espresso-windows-exe/attestations)
[![License: GPL-2.0+ (QE upstream)](https://img.shields.io/badge/License-GPL--2.0%2B-3DA639)](https://github.com/QEF/q-e)

**Native • High-Performance • Trusted Builds**

Precompiled **Quantum ESPRESSO** binaries for **Windows** — built natively with **Intel oneAPI**, **Intel MKL**, **OpenMP**, and **Microsoft MPI**.  
Maintained by the **QMatSuite** project.

**Download → unzip → run.**  
No WSL. No MinGW. No fragile toolchains.

## Why this matters

Running Quantum ESPRESSO on Windows has historically been painful:

- **Windows is not a first-class platform** for QE upstream
- **Native builds are hard**:
  - complex Fortran/C/C++ stack
  - MPI + OpenMP + math libraries
  - subtle ABI and runtime issues
- Many users gave up or accepted:
  - WSL
  - slow generic binaries
  - fragile MinGW builds
  - “it works on my machine” setups

This project changes that.

We provide a **reproducible, native, high-performance Windows build** of QE:

- Compiled with **Intel oneAPI** compilers
- Linked against **Intel MKL** (BLAS/LAPACK/FFT)
- Parallelized via **OpenMP + Microsoft MPI**
- Performance comparable to Linux builds
- No emulation, no compatibility layers

QE on Windows is now first-class and fast.

## What you get

- **Ready-to-use Windows distribution** of Quantum ESPRESSO
- **All executables and runtime DLLs colocated** under `bin/`
- **No environment setup required**
- **MPI and OpenMP supported** out of the box

This repository mirrors the standard, full-featured Windows QE bundle.

Other build variants (different QE versions, `libxc`-enabled builds, tuning experiments, etc.) are produced and documented in the toolchain repository:

- [QMatSuite Toolchain](https://github.com/QMatSuite/qmatsuite-toolchain)

## Download

**Latest standard release (recommended):**

- **Release page**: [qe-7.5-win-oneapi-msmpi](https://github.com/QMatSuite/quantum-espresso-windows-exe/releases/tag/qe-7.5-win-oneapi-msmpi)
- **Asset**: `qe-7.5-win-oneapi-msmpi.zip`
- **SHA256**: `E50EC7368A5B7A964EB5084E0A13464BA2628D4E147C16227E876002EA34FDF7`

This is the default, stable, high-performance Windows build:

- Full QE executable set
- Intel MKL backend
- OpenMP enabled
- Microsoft MPI included
- Signed and verified (see below)

For experimental or alternative builds, see:

- [QMatSuite Toolchain](https://github.com/QMatSuite/qmatsuite-toolchain)

Or open an issue if you need a custom build.

## Quick start (Windows)

Download and unzip:

- `qe-7.5-win-oneapi-msmpi.zip`

Open **PowerShell** and go to `bin\`:

```powershell
cd path\to\qe\bin
```

Run QE:

```powershell
.\pw.exe -in input.in > output.out
```

**MPI example:**

```powershell
mpiexec -n 4 .\pw.exe -in input.in
```

That’s it.

## Performance notes

- **BLAS / LAPACK / FFT**: Intel MKL
- **Threading**: OpenMP
- **MPI**: Microsoft MPI (native Windows)

You can control threading via:

- `OMP_NUM_THREADS`
- `MKL_NUM_THREADS`

This is a native Windows build, not a compatibility layer.

## Trust & verification

These binaries are not just precompiled — they are verifiable:

- **All executables are Microsoft Trusted-Signed**
  - No SmartScreen warnings
- **Built on GitHub official runners**
- **GitHub Artifact Attestation**
  - You can verify the exact commit and workflow that produced the ZIP
- **SHA256 checksums provided**

This is a reproducible and auditable build, not a random binary drop.

### Attestations (mirroring + build provenance)

- **Mirror attestation (this repo)**: proves the ZIP was downloaded + verified and then mirrored with attestation in this repository  
  - Attestations list: https://github.com/QMatSuite/quantum-espresso-windows-exe/attestations
- **Build attestation (toolchain repo)**: provenance for the build workflow that produced the ZIP  
  - https://github.com/QMatSuite/qmatsuite-toolchain/attestations/15597094

## Relation to QMatSuite

This repository is part of the **QMatSuite** ecosystem.

**QMatSuite** is a GUI and workflow manager for quantum materials simulations. These QE binaries are used as the **default Windows backend** for QMatSuite.

QMatSuite can automatically:

- download
- verify
- configure
- run QE on Windows

- [QMatSuite](https://github.com/QMatSuite/qmatsuite)

If you want a GUI instead of typing inputs by hand, QMatSuite is the natural next step.

## License

- **Quantum ESPRESSO** is licensed under **GPL v2 or later**
- This repository redistributes **unmodified QE binaries**
- Third-party runtime licenses are included under `licenses/`

## Bottom line

Quantum ESPRESSO on Windows is no longer a compromise.

This project delivers:

- Native performance
- Reproducible builds
- Trusted binaries
- Zero setup

Download, run, compute.
