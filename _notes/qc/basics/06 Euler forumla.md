---
title: 06 Euler Formula
domain: qc
topic: basics
tags:
  - euler-formula
  - phase
  - complex-numbers
updated: 2026-06-02
---

### 1. The Role of Euler’s Formula in Representing Complex Numbers

At the heart of quantum mechanics lies the need to describe states as complex vectors. Any complex number can be expressed in *polar form* using Euler’s formula:

```math
e^{i\phi} = \cos \phi + i \sin\phi.
```

This representation offers a compact way to capture both the magnitude and the phase of a complex number. For a normalized number (one with magnitude 1), the entire content is in the phase $\phi$. Since the relative phase is the quantity that matters in quantum mechanics, $e^{i\phi}$ becomes the natural choice.

---

### 2. Mapping to the Bloch Sphere: Azimuthal Angle $\phi$

When we write a qubit state as

```math
|\psi\rangle = \cos\left(\frac{\theta}{2}\right) |0\rangle + e^{i\phi}\sin\left(\frac{\theta}{2}\right)|1\rangle,
```

we are parameterizing the state in a way that beautifully matches spherical coordinates:

- **Polar Angle ($\theta$)** determines the probability distribution between $|0\rangle$ and $|1\rangle$—essentially the "latitude" on the Bloch sphere.
- **Azimuthal Angle ($\phi$)** describes the orientation around the z-axis—the "longitude." This angle captures the relative phase between the components.

By writing the coefficient of $|1\rangle$ as $e^{i\phi}\sin\left(\frac{\theta}{2}\right)$, the phase factor $e^{i\phi}$ directly encodes the relative phase. Two states with the same probability amplitudes (same $\theta$) but different $\phi$ values will lie on the same circle of latitude on the Bloch sphere yet be rotated relative to each other. This rotation reflects a difference in the phase relationship between $|0\rangle$ and $|1\rangle$.

---

### 3. Why Use $e^{i\phi}$ Specifically?

- **Conciseness and Clarity:**  
  Euler’s formula lets us write the phase succinctly. Instead of writing out separate sine and cosine terms or handling the phase as a separate additive parameter, $e^{i\phi}$ elegantly combines both into one term.
  
- **Natural Representation for Unitary Operations:**  
  Unitary evolution in quantum mechanics (such as time evolution or the action of quantum gates) is dominated by exponentials. For example, time evolution is given by $e^{-iHt/\hbar}$. Using $e^{i\phi}$ in the state’s representation mirrors that structure, making it straightforward to see how phases evolve or combine.
  
- **Reflecting the Geometry:**  
  On the Bloch sphere, rotations are the way we interpret state changes. Using $e^{i\phi}$ to denote the phase means that varying $\phi$ rotates the state around the z-axis. This rotation is what you’d expect if you’re moving along a circle of fixed latitude (fixed $\theta$).

- **Conventional and Universal:**  
  The use of Euler’s number $e$ in the exponent is standard in mathematics and physics when dealing with periodic phenomena. It links to Fourier analysis, wave mechanics, and many other domains, so it’s a natural choice for expressing the idea of a “phase” that repeats every $2\pi$.

---

### In Summary

- **Why the Azimuthal Angle $\phi$?**  
  It captures the relative phase between state components—an essential part of interference effects and quantum operations.
  
- **Why $e^{i\phi}$ and not another notation?**  
  Because Euler’s formula, $e^{i\phi} = \cos \phi + i\sin\phi$, provides a neat, compact, and mathematically natural way to encapsulate phase information. It directly ties into how we understand rotations in the complex plane, which is central to the behavior of quantum states.

This combination of conceptual clarity and mathematical elegance is why the qubit is naturally described in this manner on the Bloch sphere.

---

1. **Euler’s Formula:**  
   Euler’s formula states that for any real number $\phi$,  

  ```math
  e^{i\phi} = \cos\phi + i\sin\phi
  ```

   This formula is a foundational result in complex analysis. It provides a compact and elegant way to express any point on the unit circle in the complex plane using the angle $\phi$.

2. **Natural Choice of Base:**  
   The exponential function is defined with base $e$ (approximately 2.71828) because of its many pleasant mathematical properties—especially its behavior under differentiation (its derivative is itself). While we could define exponentials with other bases, $e$ is the natural and conventional choice. Thus, $e^{i\phi}$ naturally encodes the phase $\phi$ as both cosine and sine contributions.

3. **Relative Phase Representation:**  
   In the expression for a qubit,

  ```math
  |\psi\rangle = \cos\left(\frac{\theta}{2}\right) |0\rangle + e^{i\phi}\sin\left(\frac{\theta}{2}\right)|1\rangle,
  ```

   the term $e^{i\phi}$ assigns a relative phase to the $|1\rangle$ state. This phase is critical for understanding interference and other quantum phenomena. The use of $e^{i\phi}$ is simply a concise way to capture this phase information—thanks directly to Euler’s formula.

4. **No Extra Physical Meaning to 2.71828:**  
   The number $e = 2.71828\ldots$ is not special because of its numeric value in this context. It’s not like we are “tuning” a qubit with the number 2.71828; instead, the exponential function with base $e$ is the standard mathematical tool to express rotations in the complex plane. The importance is in the structure it provides (rotations and oscillatory behavior), not in the particular digits of $e$.

---

### In Summary

The use of $e^{i\phi}$ arises because Euler’s formula:

```math
e^{i\phi} = \cos\phi + i\sin\phi
```

gives a natural way to represent points on the unit circle. This is directly applicable to encoding the relative phase of quantum states. The base $e$ is chosen for mathematical convenience and because it inherently emerges in the study of continuous transformations and differential equations—not because the numerical value 2.71828 has a direct physical interpretation in the qubit’s behavior.

Would you like to delve deeper into how the properties of $e^{i\phi}$ lead to practical outcomes in quantum interference or explore other aspects of the Bloch sphere representation further?
