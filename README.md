# Approximate Quantum Fourier Transform in Qrisp

A Qiskit implementation of the T-count reduction method for the Approximate Quantum Fourier Transform (AQFT) presented by Park and Ahn.

---

## Overview

This project implements the **Approximate Quantum Fourier Transform (AQFT)** in Qiskit based on the techniques presented in:

> **Park, B., & Ahn, D.** *Reducing T-count and T-depth in Approximate Quantum Fourier Transform Circuits*. *Scientific Reports*, **15**, 37199 (2025). https://doi.org/10.1038/s41598-025-21087-2

The goal of this project is to reproduce the **T-count reduction** method described in the paper using Qiskit.

---

## Why We Do It

The Quantum Fourier Transform (QFT) is a fundamental component of many quantum algorithms, including Quantum Phase Estimation, Shor's factoring algorithm, and the Harrow–Hassidim–Lloyd (HHL) algorithm. In fault-tolerant quantum computing, however, non-Clifford gates—particularly **T gates**—are significantly more expensive to implement than Clifford gates.

Reducing the **T-count** of QFT circuits is therefore an important optimization for practical fault-tolerant quantum computing. This project implements the T-count reduction technique proposed by **Park and Ahn (2025)** while preserving the functionality of the original AQFT circuit.

---

**Note:** This project implements the **6-qubit** version of the Approximate Quantum Fourier Transform (AQFT) to demonstrate the core ideas of the T-count reduction technique. The goal is to provide the smallest non-trivial implementation that is easy to understand, verify, and build upon.

For the purposes of this notebook, we generated a random 6-qubit circuit to illustrate the (n)-qubit case with (n=6). However, the methods presented in **Park and Ahn (2025)** are not limited to this circuit size. The implementation can be extended to larger AQFT circuits by applying the same construction and optimization techniques.

## How We Do It

This implementation follows **AQFT Circuit 1** from **Park and Ahn (2025)** and reproduces its T-count optimization using **Qrisp**.

The technical details include:

* The use of **Gidney's quantum adder** as the arithmetic building block.
* We assume access to the prepared Fourier-basis resource state `|ψ_b⟩ = QFT|1⟩_b`. In this notebook, we synthesize `|ψ_b⟩` directly using the QFT rather than implementing its fault-tolerant preparation. In practice, this state can be prepared using a **Repeat-Until-Success (RUS)** method, such as that presented by **Bocharov, Roetteler, and Svore (2015)** and implemented in the Microsoft Quantum sample repository: https://github.com/microsoft/quantum/tree/main/samples/algorithms/repeat-until-success.
* **Dummy register for the inverse PGT:** We initialize an auxiliary register in the `|0⟩` state and strategically apply Z gates to simulate the inverse PGT operation described by **Park and Ahn (2025)**, which is crucial for reducing the T-count.

  
## Future Work

Possible extensions of this project include:

* Implementing the **T-depth reduction** described in **Park and Ahn, (AQFT Circuit 2)**.
* Further simplifying single-qubit unitary decompositions using Clifford+T synthesis.
* Benchmarking larger AQFT circuits and comparing them with other QFT implementations.
* Evaluating the trade-off between approximation error and T-count reduction across different quantum algorithms.

---

## References

1. Park, B., & Ahn, D. (2025). **Reducing T-count and T-depth in Approximate Quantum Fourier Transform Circuits.** *Scientific Reports*, **15**, 37199. https://doi.org/10.1038/s41598-025-21087-2

2. Gidney, C. (2018). **Halving the Cost of Quantum Addition.** *Quantum*, **2**, 74. https://doi.org/10.22331/q-2018-06-18-74

3. Bocharov, A., Roetteler, M., & Svore, K. M. (2015). **Efficient Synthesis of Universal Repeat-Until-Success Circuits.** *Physical Review Letters*, **114**(8), 080502. https://doi.org/10.1103/PhysRevLett.114.080502
