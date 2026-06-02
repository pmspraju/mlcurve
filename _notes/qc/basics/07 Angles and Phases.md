---
title: 07 Angles and Phases
domain: qc
topic: basics
tags:
  - angles
  - phases
  - bloch-sphere
updated: 2026-06-02
---

Let's break it down:

---

### 1. The Polar Angle (θ) and the Azimuthal Angle (φ)

When we use the Bloch sphere to represent a qubit's state, we're effectively describing a point on the surface of a sphere using **spherical coordinates**. In these coordinates:

- **Polar Angle (θ):**  
  - This is the angle between the Bloch vector (the point representing the qubit) and the positive z-axis.  
  - It ranges from 0 to π (0° to 180°).  
  - Physically, when θ = 0, the qubit state corresponds to the north pole, which we associate with the basis state |0⟩. When θ = π, the state is at the south pole—corresponding (up to an irrelevant global phase) to the state |1⟩.
  
- **Azimuthal Angle (φ):**  
  - This angle tells you how the projected vector in the xy-plane is oriented with respect to the x-axis.  
  - φ ranges from 0 to 2π (0° to 360°).  
  - It captures the "twist" or rotation around the z-axis. In the quantum context, this directly relates to the *relative phase* between the basis state's amplitudes.
  
Imagine the Bloch sphere like Earth:  
- The **polar angle θ** is like the latitude (but measured from the North Pole rather than the equator).  
- The **azimuthal angle φ** is like the longitude.  

In Cartesian coordinates, a point on the sphere is given by:  
```math
(x, y, z) = (\sin\theta\cos\phi,\; \sin\theta\sin\phi,\; \cos\theta).
```

---

### 2. Why Is the Relative Phase \($ e^{i\phi} \)$ Needed for the State \($|1\rangle\)$?

Quantum states are expressed as superpositions, and a general qubit state is written as

```math
|\psi\rangle = \alpha |0\rangle + \beta |1\rangle,
```

with a normalization condition \($ |\alpha|^2 + |\beta|^2 = 1 \)$. Because of a fundamental property of quantum mechanics, an overall global phase (a common factor multiplying the entire state) is physically unobservable. Therefore, we can choose a convention where one amplitude (typically \($\alpha\)$ ) is a positive real number. This leaves any physically meaningful phase difference to be associated with the other amplitude, \($\beta\)$.

By writing the amplitudes as

```math
\alpha = \cos\left(\frac{\theta}{2}\right), \quad \beta = e^{i\phi}\sin\left(\frac{\theta}{2}\right),
```

we ensure:

- **Normalization Automatically Holds:**  
  The identity
```math
\cos^2\left(\frac{\theta}{2}\right) + \sin^2\left(\frac{\theta}{2}\right) = 1
```  
  guarantees that the state is normalized without extra effort.

- **Encoding the Relative Phase:**  
  The factor \($ e^{i\phi} \)$ attached to the \($|1\rangle\)$ amplitude captures the *relative phase* between \($|0\rangle\)$ and \($|1\rangle\)$. This phase difference is crucial because:
  - **Interference Effects:**  
    The outcomes of many quantum processes—like interference in a quantum circuit, entanglement, or even simple measurement probabilities—depend entirely on the difference in phase between the two components, not on their overall phase.
  - **State Distinction:**  
    Consider two states:
    
```math
\frac{|0\rangle + |1\rangle}{\sqrt{2}} \quad \text{and} \quad \frac{|0\rangle - |1\rangle}{\sqrt{2}}.
```

   They have the same probability amplitudes (i.e., equal absolute values) for being in \($|0\rangle\)$ or \($|1\rangle\)$, yet they lead to very different behaviors in interference experiments because the relative phase (0 vs. π) between the two components is different.
  - **Geometric Interpretation:**  
    On the Bloch sphere, changing φ rotates the point around the z-axis. This rotation reflects the variation in the relative phase without changing the probability of obtaining \($|0\rangle\)$ or \($|1\rangle\)$ (which depends only on θ), but it does affect the way the state interferes with others.

---

### Bringing It Together

The general qubit state

```math
|\psi\rangle = \cos\left(\frac{\theta}{2}\right)|0\rangle + e^{i\phi}\sin\left(\frac{\theta}{2}\right)|1\rangle
```

uses spherical coordinates:
- **θ (polar)** fixes the probability weight between the basis states (i.e., the "latitude" on the sphere).
- **φ (azimuthal)** specifies the relative phase attached to \($|1\rangle\)$, which is essential for capturing the quantum interference effects and the full range of transformation allowed by quantum mechanics.

#### ASCII Diagram for Visualization

```
             Polar Angle (θ)
                  ↑
                  |
           (North Pole)
      |0⟩      *      
         \         \
          \         \
           \         \
            \         \
             \         \
       --------------------→   Azimuthal rotation (φ)
             /         /
            /         /
           /         /
          /         /
         /         /
    (South Pole)
         |1⟩  *
```

- The vertical direction (z-axis) is determined by the polar angle θ.
- The horizontal rotation around the z-axis is determined by the azimuthal angle φ.
- The \($ e^{i\phi} \)$ term in \($|1⟩\)$ enables the state to “twist” in the plane perpendicular to the z-axis, embodying the essence of quantum phase.

---

### Further Thoughts

Understanding these angles helps explain not just static properties, but also how quantum gates (which act as rotations on the Bloch sphere) modify the state. For instance, changing φ rotates the state around the z-axis, while modifying θ adjusts the probability distribution between \($|0⟩\)$ and \($|1⟩\)$.

Exactly. The Bloch sphere is a geometric representation of a qubit state, and it uses spherical coordinates to capture both the amplitudes and the relative phase between the basis states. Here's how it works:

1. **Same Amplitudes with Different Azimuthal Angles:**  
   In a spherical coordinate system, two vectors can have the same "latitude" (i.e., the same polar angle, θ) but differ in their "longitude" (i.e., the azimuthal angle, φ). For the qubit state  
```math
|\psi\rangle = \cos\left(\frac{\theta}{2}\right)|0\rangle + e^{i\phi}\sin\left(\frac{\theta}{2}\right)|1\rangle,
```
   having the same polar angle means the probabilities of measuring \($|0\rangle\)$ versus \($|1\rangle\)$ are the same. However, if the azimuthal angle φ is different, the relative phase between the basis components is different.

2. **Role of the Relative Phase \($ e^{i\phi} \)$:**  
   The term \($ e^{i\phi} \)$ attaches a phase factor to the \($|1\rangle\)$ component. This phase difference is significant even though it doesn’t change the measurement probabilities in the computational basis (since those depend only on the magnitudes \($\cos^2\left(\frac{\theta}{2}\right)\)$ and \($\sin^2\left(\frac{\theta}{2}\right)\)$). Instead, the relative phase becomes crucial in scenarios involving quantum interference or the application of quantum gates. For instance, when combining two qubit states or passing a state through a quantum circuit, two vectors with the same amplitudes but different azimuthal angles will interfere differently due to that \($ e^{i\phi} \)$ factor.

3. **Visualizing on the Bloch Sphere:**  
   - **Polar Angle (θ):** Determines the “height” of the state on the sphere, directly relating to the probabilities of \($|0\rangle\)$ and \($|1\rangle\)$.  
   - **Azimuthal Angle (φ):** Determines the rotation around the vertical (z) axis, capturing the relative phase of the \($|1\rangle\)$ component relative to \($|0\rangle\)$.  
     
   Two states with the same θ but differing φ are like two points on the same "latitude circle" of the sphere. They have the same "vertical" projection (hence the same probabilities for \($|0\rangle\)$ and \($|1\rangle\)$), but they are rotated relative to each other around the z-axis. This rotation encodes the relative phase difference.

4. **Why It Matters:**  
   While a global phase (applying the same phase factor to the entire state) is unobservable, the **relative phase** between the components \($ |0\rangle \)$ and \($ |1\rangle \)$ is measurable and affects how qubits combine, interfere, and evolve under quantum operations. This is why the phase factor \($ e^{i\phi} \)$ is essential—it tells us how the state "twists" around the sphere, influencing the behavior of interference patterns and the effects of quantum gates.

---

In summary, the relative phase difference encoded as \($ e^{i\phi} \)$ in the state's coefficient for \($|1\rangle\)$ distinguishes between two states that otherwise have the same amplitude distribution (i.e., the same polar angle). This detail is critical in quantum mechanics, providing the nuances necessary for interference and other quantum phenomena.

If you're curious, we could explore how different quantum gates rotate the Bloch sphere, modifying these angles, or dive into how interference emerges from these phase differences in multi-qubit systems.
