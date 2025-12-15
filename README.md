# Quantum ESPRESSO for Windows (.exe, ready-to-use)

✅ **Precompiled Quantum ESPRESSO (QE) executables for Windows 10/11 — just unzip and run.**  
Maintained by the [QMatSuite](https://github.com/qmatsuite/qmatsuite) project.

> This repository focuses on making **QE easy to run on Windows**,  
> with optional convenience builds for Linux and macOS later.

---

## 1. What is this?

This project provides **ready-to-use builds of Quantum ESPRESSO** for:

- Windows users who don’t want to deal with compilers, MinGW, or WSL  
- Teaching / classroom environments where students should be able to  
  *“download QE and run an example in a few minutes”*  
- GUI frontends (e.g. QMatSuite) that need a reliable QE backend

Goals:

- **No compilation**
- **No WSL required**
- **No toolchain setup** — just unzip, optionally add to `PATH`, and run `pw.x`.

---

## 2. Downloads

> ⚠️ **Precompiled packages are not published yet.**  
> The toolchain and first public release are being prepared.

Planned packages:

| Platform        | Status  | Planned package name                              | Notes                                              |
|-----------------|---------|---------------------------------------------------|----------------------------------------------------|
| Windows 64-bit  | WIP     | `qe-7.3.0-win64-qe-mkl-msmpi.zip`                 | QE with Intel oneAPI toolchain (MKL + MS-MPI + OMP)|
| macOS arm64     | planned | `qe-7.3.0-macos-arm64-qe-accelerate.tar.gz`       | QE linked against Apple's Accelerate (BLAS/LAPACK) |
| Linux x86_64    | planned | `qe-7.3.0-linux-x86_64-qe-openblas.tar.gz`        | Portable glibc + OpenBLAS                          |

When the first release is ready, this section will list:

- Direct download links  
- SHA256 checksums  
- Minimal test commands to verify the installation  

---

## 3. Quick start (Windows, planned)

Once the first Windows package is published, the workflow will look like:

1. Download `qe-7.3.0-win64-qe-mkl-msmpi.zip`
2. Extract it to e.g. `C:\QE\qe-7.3.0`
3. Open **PowerShell**:

   ```powershell
   cd C:\QE\qe-7.3.0\bin
   .\pw.x.exe < ..\examples\si_scf.in > ..\examples\si_scf.out
   ```

4. If you see SCF iterations running and the job finishes without errors,  
   your QE installation is working. The output will be written to  
   `examples\si_scf.out`.

We will ship a minimal example under `examples/` to make self-testing easy.

---

## 4. What will be included?

Planned content for the Windows bundle:

- **Quantum ESPRESSO core executables**, e.g.:
  - `pw.x`, `ph.x`, `pp.x`, `bands.x`, `dos.x`, `projwfc.x`, …
- Basic example inputs under `examples/`
- Optional small helper scripts (e.g. a self-test runner)

Windows builds are planned to use:

- **BLAS/LAPACK**: Intel MKL  
- **Parallelism**:
  - OpenMP by default  
  - Optional MS-MPI builds for users who need MPI on Windows  

macOS builds are planned to use:

- **Apple Accelerate** as the BLAS/LAPACK backend (system framework)
- OpenMP (or compiler-native threading) where appropriate

Linux builds will likely use:

- OpenBLAS (or system BLAS/LAPACK)
- OpenMP

These are mainly intended as convenience builds for users who don’t want to compile QE themselves.

---

## 5. Relation to QMatSuite

This repository is part of the **QMatSuite toolchain**:

- **QMatSuite** is a GUI and workflow manager for quantum materials simulations.  
- The QE binaries published here will be used as the **default QE backend** inside QMatSuite on Windows, and optionally on other platforms.  
- QMatSuite will be able to **download, verify, and configure** these packages automatically.

👉 QMatSuite main repo: <https://github.com/qmatsuite/qmatsuite>

If you mainly want a GUI and don’t care about build details, QMatSuite may be a better starting point.

---

## 6. Roadmap

Planned steps:

- [ ] Publish first **Windows 64-bit QE-only** build  
- [ ] Provide minimal **Linux** and **macOS** builds  
- [ ] Add GitHub Actions workflows to build and upload releases automatically  
- [ ] Ship a simple self-test script (`qe-check.ps1` / `qe-check.bat`)  
- [ ] Document performance tips (threads, MPI, antivirus interaction on Windows)  

Feedback on priorities (QE version, platforms, extra tools) is welcome via GitHub Issues.

---

## 7. License & upstream projects

- **Quantum ESPRESSO** is licensed under the GPL; see the upstream project:  
  <https://github.com/QEF-project/q-e>

This repository only provides **precompiled convenience builds** of QE.  
Licensing of the original project remains unchanged.
