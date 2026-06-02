---
title: 01 Observables
domain: qc
topic: basics
tags:
  - observables
  - operators
  - measurement
updated: 2026-06-02
---

In quantum mechanics, an **observable** is a physical quantity that can be measured—such as position, momentum, or energy. Mathematically, an observable is represented by a **Hermitian (self-adjoint) operator** acting on the Hilbert space of the quantum system. Here’s a detailed look at what observables are and how they relate to quantum systems:

---

## 1. Mathematical Representation

### Hermitian Operators
- **Definition:**  
  An operator \( \hat{A} \) is Hermitian if  
  ```math
  \hat{A} = \hat{A}^\dagger,
  ```  
  meaning it equals its own adjoint (or conjugate transpose). This property guarantees that all eigenvalues of \( \hat{A} \) are real numbers, which is essential since measurement outcomes must be real.

- **Eigenstates and Eigenvalues:**  
  For an observable \( \hat{A} \), the eigenvalue equation is:
  ```math
  \hat{A} |\phi_i\rangle = a_i |\phi_i\rangle,
  ```
  where:
  - \( |\phi_i\rangle \) are the eigenstates (or eigenvectors).  
  - \( a_i \) are the corresponding eigenvalues, which represent the possible results of measuring the observable.

### Spectral Decomposition
- **Spectral Theorem:**  
  This theorem tells us that any Hermitian operator can be decomposed in terms of its eigenstates and eigenvalues:
  ```math
  \hat{A} = \sum_i a_i |\phi_i\rangle \langle\phi_i|,
  ```
  or, for continuous spectra, as an integral. This expression shows that the operator “projects” onto its eigenstates, and it underpins how measurement probabilities are calculated via the Born rule.

---

## 2. Connection to Quantum States

### Quantum States in Hilbert Space
- **Representation:**  
  A quantum state is described by a vector \(|\psi\rangle\) in a Hilbert space. Because the eigenstates of an observable form a complete basis, the state can be expressed as:
  ```math
  |\psi\rangle = \sum_i c_i |\phi_i\rangle,
  ```
  where each \( c_i \) is a complex amplitude.

### Measurement and Probabilities
- **Outcome of a Measurement:**  
  If you measure the observable \( \hat{A} \) on the state \(|\psi\rangle\), then the only outcomes you can get are the eigenvalues \( a_i \), and the system will collapse to the corresponding eigenstate \( |\phi_i\rangle \).

- **Born Rule:**  
  The probability of obtaining the measurement result \( a_i \) is given by:
  ```math
  P(a_i) = |c_i|^2 = |\langle \phi_i|\psi\rangle|^2.
  ```
  This rule connects the mathematical description with experimental outcomes.

---

## 3. Physical Interpretation

- **Real-World Example:**  
  Consider the observable of **energy** in a quantum system. The Hamiltonian operator \( \hat{H} \) represents energy. Its eigenstates correspond to states with definite energy, and its eigenvalues are the possible energy levels of the system.

- **Observable as a “Question” to the System:**  
  You can think of an observable as the question you ask the system (e.g., "What is your energy?"). The answer you receive is one of the eigenvalues, with the system's state “choosing” a specific eigenstate in the process.

- **Determinism vs. Probabilism:**  
  - If a system is in an eigenstate of \( \hat{A} \), then measuring \( A \) gives a definite, predictable outcome.
  - In a superposition of eigenstates, the outcome is probabilistic, with probabilities given by the squared magnitudes of the amplitudes.

---

## 4. ASCII Diagram Illustration

```
             +-------------------------+
             |   Quantum States in     |
             |     Hilbert Space       |
             +-------------------------+
                        |
                        V
                   |ψ⟩ = Σ cᵢ |φᵢ⟩
                        |
                        |  (Here, |φᵢ⟩ are eigenstates of observable Â)
                        V
         +-------------------------------------+
         | Observable Operator Â (Hermitian)   |
         |   Â |φᵢ⟩ = aᵢ |φᵢ⟩ (measurable values) |
         +-------------------------------------+
                        |
                        V
         +-------------------------------------+
         | Measurement Outcome:                |
         |  outcome aᵢ with probability |cᵢ|²   |
         +-------------------------------------+
```

---

## 5. Summary

- **Observables** are physical quantities (like position, momentum, energy) represented by Hermitian operators.
- The **eigenvalues** of these operators represent the possible outcomes when you measure the observable.
- The **quantum state** is expressed as a superposition of the operator's eigenstates, and through the Born rule, the squared amplitude of each eigenstate gives the probability of that measurement outcome.
- **Hermitian operators** ensure that the measurement outcomes are real, which corresponds to the physical values observed in experiments.

This framework bridges the gap between the abstract mathematics of quantum theory and the tangible results of laboratory measurements. If you’re intrigued by how operators evolve in time or how non-commuting observables lead to uncertainty principles, we can dive into those subjects next.
