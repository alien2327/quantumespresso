# Quantum Espresso tutorial
Quantum Espresso(QE) tutorial and example datas

[원문](http://www.quantum-espresso.org/resources/users-manual)

# Wiki
## Core packages
다음은 QE의 코어 패키지 리스트입니다. QE 코어 패키지는 [범함수이론(Density-Functional Theory, DFT)](https://en.wikipedia.org/wiki/Density_functional_theory)으로 전자구조를 계산하고, [평면파 기저(Plane-Wave basis sets)](https://www.tcm.phy.cam.ac.uk/castep/documentation/WebHelp/content/modules/castep/thcastepplanebasis.htm)와 [유사 퍼텐셜(pseudopotentials)](https://en.wikipedia.org/wiki/Pseudopotential)를 사용합니다. [추가1](https://nwchemgit.github.io/pw-lecture.pdf) [추가2](https://www.phenix.cnrs.fr/IMG/pdf/dft-pw.pdf)

- PWscf (PW) : Plane-Wave Self-Consistent Field
   - ground-state energy and one-electron (Kohn-Sham) orbitals, atomic forces, stresses;
   - structural optimization, also with variable cell;
   - molecular dynamics on the Born-Oppenheimer surface, also with variable cell;
   - macroscopic polarization (and orbital magnetization) via Berry Phases;
   - various forms of finite electric fields, with a sawtooth potential or with the modern theory of polarization;
   - Effective Screening Medium (ESM) method;
   - self-consistent continuum solvation (SCCS) model, need patched with [ENVIRON](http://www.quantum-environ.org/);
- CP (CPV): Car-Parrinello Molecular Dynamics
   - Car-Parrinello molecular dynamics;
   - variable-cell dynamics;
   - free-energy surface calculation at fixed cell through meta-dynamics, need patched with [PLUMED](https://www.plumed.org/); 

## Specialized packages
QE는 특정 목적에 특화된 추가 패키지를 제공합니다.

- PWneb (NEB) : energy barriers and reaction pathways through the Nudged Elastic Band method
   - using PWscf package as computing engine;
   - calculates reaction barriers and pathways (neb.x);
   - generates a reaction path, by interpolating the supplied path (path_interpolation.x);
- PHonon : phonons with Density-Functional Perturbation Theory
- PostProc (PP) : various utilities for data postprocessing
- PWcond : ballistic conductance
- GWL: GW calculations and solution of the Bethe-Salpeter Equation
- XSPECTRA : K-edge X-ray adsorption spectra
- TDDFPT : calculations of spectra using Time-Dependent Density-Functional Perturbation Theory
- EPW : electron-phonon calculations using Wannier functions

## Auxiliary packages
QE는 GUI 등을 사용 가능한 보조 패키지를 제공합니다.
- PWgui : a Graphical User Interface, producing input data files for PWscf
- atomic : a program for atomic calculations and generation of pseudopotentials

## Additional packages (may need additional install)
추가로 다음 패키지도 사용가능합니다. 단, 아래 패키지를 사용하기 위해서는 QE 초기 설정시 추가 패키지를 설치하도록 Makefile을 수정할 필요가 있습니다.

- GIPAW (Gauge-Independent Projector Augmented Waves): NMR chemical shifts and EPR g-tensor
- WANNIER90 : maximally localized Wannier functions
- WanT: quantum transport properties with Wannier functions
- YAMBO: electronic excitations within Many-Body Perturbation Theory: GW and Bethe-Salpeter equation
- PLUMED: calculation of free-energy surface through metadynamics
