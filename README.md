# Approximate Quantum Fourier Transform in Qiskit

A Qiskit implementation of the T-count reduction method for the Approximate Quantum Fourier Transform (AQFT) presented by Park and Ahn.

---

## Overview

This project implements the **Approximate Quantum Fourier Transform (AQFT)** in Qiskit based on the techniques presented in:

> **Park, B., & Ahn, D.** *Reducing T-count and T-depth in Approximate Quantum Fourier Transform Circuits*. *Scientific Reports*, **15**, 37199 (2025). https://doi.org/10.1038/s41598-025-21087-2

The goal of this project is to reproduce the **T-count reduction** method described in the paper using Qiskit.

---

## Why We Do It

The Quantum Fourier Transform (QFT) is a fundamental component of many quantum algorithms, including Quantum Phase Estimation, Shor's factoring algorithm, and the Harrow–Hassidim–Lloyd (HHL) algorithm. In fault-tolerant quantum computing, however, non-Clifford gates—particularly **T gates**—are significantly more expensive to implement than Clifford gates.

Reducing the **T-count** of QFT circuits is therefore an important optimization for practical fault-tolerant quantum computing. This project implements the T-count reduction technique proposed by Park and Ahn while preserving the functionality of the original AQFT circuit.

---

## How We Do It

This implementation follows **AQFT Circuit 1** from the paper and reproduces its T-count optimization in Qiskit.

The implementation includes:

* Implementation of **AQFT Circuit 1** described in the paper.
* Implementation of the paper's **T-count reduction** method.
* Use of **Gidney's quantum adder** as the arithmetic building block.
* Resource analysis and comparison with the standard QFT implementation.

---

## Future Work

Possible extensions of this project include:

* Implementing the paper's **T-depth reduction** (AQFT Circuit 2).
* Further simplifying single-qubit unitary decompositions using Clifford+T synthesis.
* Investigating more efficient Clifford+T synthesis algorithms for arbitrary single-qubit rotations.
* Developing automated Clifford+T optimization passes for Qiskit.
* Benchmarking larger AQFT circuits and comparing them with other QFT implementations.
* Evaluating the trade-off between approximation error and T-count reduction across different quantum algorithms.

---

## References

1. Park, B., & Ahn, D. (2025). *Reducing T-count and T-depth in Approximate Quantum Fourier Transform Circuits*. **Scientific Reports**, 15, 37199. DOI: 10.1038/s41598-025-21087-2.

2. [Reducing T-count and T-depth in Approximate Quantum Fourier Transform Circuits (Nature)](https://www.nature.com/articles/s41598-025-21087-2?utm_source=chatgpt.com)
