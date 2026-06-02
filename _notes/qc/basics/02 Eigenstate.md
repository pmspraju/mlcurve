---
title: 02 Eigenstate
domain: qc
topic: basics
tags:
  - eigenstates
  - operators
  - measurement
updated: 2026-06-02
---

An eigenstate is a state that satisfies the equation

```math
\hat{O}|\psi\rangle = \lambda|\psi\rangle,
```

for some operator \(\hat{O}\) (often representing an observable) and eigenvalue \(\lambda\). In many quantum mechanics problems, particularly when dealing with observables, we choose the eigenstates as the basis for the Hilbert space because they have a direct physical meaning—the measurement of the observable always yields one of its eigenvalues, and the system "collapses" into the corresponding eigenstate.

However, saying that an eigenstate is "the same as" one of the basis states requires some clarification:

1. **Eigenstates as a Natural Basis:**  
   When an observable is represented by a Hermitian operator, its eigenstates (if they form a complete set) can be chosen as an orthonormal basis for the Hilbert space. In this sense, they *are* the basis states in which we express any state of the system for the purpose of making measurements related to that observable.

2. **Basis Choice is Not Unique:**  
   The Hilbert space admits many different complete bases. While the eigenstates of a particular operator provide a natural basis for discussing measurements of that operator, they are just one of many possible choices. For example, you could also choose a momentum basis, a position basis, or any other set of complete states even if those states might not be eigenstates of the observable you're considering.

3. **Degenerate Eigenstates:**  
   In cases where an eigenvalue has a degeneracy (i.e., there are multiple independent eigenstates corresponding to the same eigenvalue), you can choose any orthonormal set of states spanning that degenerate subspace as basis states. So while each chosen vector in that basis is an eigenstate, the choice among them is not unique.

4. **Operational Significance:**  
   In practice, when you measure an observable, the eigenstates of that observable dictate which outcomes are possible—the Born rule tells you that the probability of measuring a particular eigenvalue is given by the squared magnitude of the amplitude of the state when expressed in that eigenbasis.

### ASCII Diagram Illustration

```
                        |ψ⟩ (An arbitrary state)
                               |
                               V
         Expand |ψ⟩ in the eigenbasis of observable Ō
                               |
              +--------------+--------------+
              |              |              |
         |eigenstate₁⟩   |eigenstate₂⟩   ... |eigenstate_n⟩
              |              |              |
              V              V              V
  Ō|eigenstate_i⟩ = λᵢ |eigenstate_i⟩   (Each eigenstate has a definite measurement outcome)
```

### Summary

- **Eigenstate:**  
  A state that, when acted on by an operator, yields a scalar multiple of itself. For a Hermitian operator (like an observable), these eigenstates have real eigenvalues.

- **Basis State:**  
  Any state in a set that spans the Hilbert space. When the basis is chosen as the eigenstates of an observable, they directly correspond to the possible measurement outcomes.

- **Connection in Quantum Mechanics:**  
  By expressing an arbitrary state in the eigenbasis of an observable, you can immediately read off the probabilities of different measurement outcomes as per the Born rule. While this eigenbasis is convenient and physically meaningful, it’s just one of many valid bases for the space.

---

Eigenstates stand out because they are *tailor-made* to a specific observable—meaning they satisfy a characteristic equation that yields a definite measurement outcome. Let’s break down the differences:

---

### 1. Eigenstates Are Defined by an Operator

For a given operator \( \hat{O} \) (which represents an observable in quantum mechanics), an eigenstate \(|\psi\rangle\) satisfies:

```math
\hat{O} |\psi\rangle = \lambda |\psi\rangle,
```

where \(\lambda\) is the eigenvalue associated with that eigenstate. This means that if your system is in an eigenstate of \(\hat{O}\), then a measurement of the observable corresponding to \(\hat{O}\) will definitely return the value \(\lambda\).

---

### 2. Definite Outcome vs. Probabilistic Superposition

- **Eigenstates:**  
  When your state is an eigenstate of an observable, the outcome is *certain*. For instance, if you're measuring the spin of a particle along the z-axis and your particle is in an eigenstate of the spin-z operator, you'll definitely get either \(+\frac{1}{2}\) or \(-\frac{1}{2}\) depending on which eigenstate it is.

- **General State Vectors:**  
  A general state vector can be any vector in the Hilbert space, which might be a *superposition* of multiple eigenstates. Consider a state like:
  
  ```math
  |\psi\rangle = \alpha |e_1\rangle + \beta |e_2\rangle,
  ```
  
  where \( |e_1\rangle \) and \( |e_2\rangle \) are eigenstates of the observable \( \hat{O} \). In this case, a measurement doesn’t yield a definite outcome; instead, you obtain \( e_1 \) with probability \(|\alpha|^2\) and \( e_2 \) with probability \(|\beta|^2\).

---

### 3. Basis Choice and Uniqueness

- **Eigenstate Basis:**  
  For any Hermitian operator, you can construct a complete, orthonormal set of eigenstates that spans the entire Hilbert space. This eigenbasis is particularly useful when you are measuring the observable associated with the operator because it directly maps to the possible outcomes.

- **General State Basis:**  
  While eigenstates can form a basis, a general state vector does not need to be aligned with any specific operator’s eigenstates. Instead, it can be expressed in *any* complete basis. The particular choice of basis depends on the observable or the problem at hand.

---

### 4. Visualization with an ASCII Diagram

Here’s an ASCII diagram to illustrate the difference:

```
             General State Vector
             --------------------
                 |ψ⟩ = α|e₁⟩ + β|e₂⟩ + ...       
                         |
                         | Expressed in terms of eigenstates of O
                         V
           +-----------------------------+
           | Eigenstates of the observable|
           |    |e₁⟩ with eigenvalue λ₁     |
           |    |e₂⟩ with eigenvalue λ₂     |
           |     ...                      |
           +-----------------------------+
```

- **If** |ψ⟩ is exactly one of the eigenstates, say \(|e₁⟩\), then measurement of \( \hat{O} \) will yield the outcome \(\lambda_1\) with certainty.

- **If** |ψ⟩ is a superposition, then the outcome is probabilistic, as only upon measurement does the system "collapse" onto one of the eigenstates with the probability determined by the amplitude squared.

---

### Summary

- **Eigenstates** are *special* state vectors crafted for a particular operator. They yield a definite measurement outcome (the eigenvalue) because they satisfy \( \hat{O}|\psi\rangle = \lambda|\psi\rangle \).
- **General state vectors** can be any vector in the Hilbert space. They might be a superposition of eigenstates, so when measured, they only offer a probabilistic set of outcomes rather than a definite one.

This distinction is fundamental in quantum mechanics because it underpins how measurements collapse a quantum state into a specific eigenstate, giving rise to the probabilistic nature of quantum outcomes.

---
