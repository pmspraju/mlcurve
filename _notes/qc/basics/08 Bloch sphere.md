---
title: 08 Bloch Sphere
domain: qc
topic: basics
tags:
   - bloch-sphere
   - qubits
   - geometry
updated: 2026-06-02
---

The state of a qubit is much more than a simple bit—it’s a quantum state that can exist as a superposition of two basis states. Geometrically, we represent a **pure state** of a qubit as a point on the surface of a unit sphere known as the **Bloch sphere**. This visualization not only makes the abstract mathematical state more intuitive but also neatly translates many quantum phenomena into geometric language.

---

### The Qubit State on the Bloch Sphere

A qubit’s state can be written in its most general form as:
```math
|\psi\rangle = \cos\left(\frac{\theta}{2}\right) |0\rangle + e^{i\phi}\sin\left(\frac{\theta}{2}\right) |1\rangle,
```
where:

- \($\theta$\) is the *polar angle* (ranging from 0 to \($\pi$\)) ,
- \($\phi$\) is the *azimuthal angle* (ranging from 0 to \($2\pi$\)) .

**Interpretation:**

- The North Pole of the sphere (\($\theta = 0$\))  corresponds to the quantum state \($|0\rangle$\).
- The South Pole (\($\theta = \pi$\))  corresponds to the state \($|1\rangle$\).
- Any point on the surface represents a possible pure state of the qubit.

Because of the normalization condition and the fact that an overall phase is physically unobservable, any pure state can be uniquely represented by these two angles. The sphere’s surface, therefore, becomes a compact, all-encompassing picture of a qubit.

---

### How the Bloch Sphere Aids Understanding

1. **Visualization of Superposition & Interference:**
   - Every point on the sphere (except the poles)  represents a superposition of \($|0\rangle$\) and \($|1\rangle$\).
   - The angles \($\theta$\) and \($\phi$\) determine the "weight" and the relative phase between the basis states. This intuitively explains interference phenomena in quantum mechanics.

2. **Mapping Quantum Gates to Rotations:**
   - Any **single-qubit quantum gate** (which is a unitary transformation)  can be visualized as a rotation of the vector on the Bloch sphere.
   - For example:
     - The **Pauli-X gate** acts like a 180° rotation about the X-axis, flipping the state from one pole to the other.
     - The **Hadamard gate** corresponds to a rotation that brings a state from a pole to an equatorial point, creating a balanced superposition.
     
   This geometric picture makes it easier to see how quantum operations affect the state—rather than dealing with complex matrices, you can think of them as simple rotations in 3D space.

3. **Intuition for Measurement Outcomes:**
   - When you measure the qubit in the computational basis \($\{|0\rangle, |1\rangle\}$\), the probabilities are related to the projection of the state’s vector onto the Z-axis.
   - The closer the vector is to the North Pole, the higher the probability of obtaining \($|0\rangle$\) upon measurement, and vice versa for \($|1\rangle$\).

---

### An ASCII Diagram of the Bloch Sphere

Below is a simplified ASCII representation of the Bloch sphere that maps these ideas:

```
                           | Z
                           |
                         (0,0,1) 
                           |
                           |  <-- North Pole (|0⟩) 
                           |
                -----------------------
               /                      \
              /                        \
             /       • (θ,φ)           \
            |                          |
             \                        /
              \                      /
               \---------------------/
                           |
                           |
                         (0,0,-1) 
                           |
                           |  <-- South Pole (|1⟩) 
                           |
                <------- X-axis ------->
                           |
                   (Y-axis coming out of page) 
```

- The point marked • at coordinates \($(\theta, \phi) $\) represents a general qubit state.
- The poles represent the basis states \($|0\rangle$\) and \($|1\rangle$\).
- The X and Y axes provide a reference for the direction of the qubit’s phase information.

---

### Broader Implications

Using the Bloch sphere, one gains:
- **Deeper insight** into the evolution of quantum states, as quantum gate operations turn into simple rotations.
- **Enhanced intuition** on how quantum interference works, since differences in phase (represented by \($\phi$\))  directly affect the state’s position.
- A framework to **conceptualize decoherence**: while pure states lie on the surface, mixed states can be thought of as points inside the sphere, providing a clear visualization of state purity.

---

#### if base states are orthonormal, then the angle between them should be 90. But the polar angle is 180 ?

The key to resolving this apparent discrepancy lies in the different ways we measure "angles" in Hilbert space versus on the Bloch sphere. Let’s break it down:

---

### 1. **Hilbert Space and Orthonormality**

In the Hilbert space description, the computational basis states \($|0\rangle$\) and \($|1\rangle$\) are defined to be orthonormal, meaning  
```math
\langle 0 | 1 \rangle = 0.
```  
When we use the Fubini–Study metric—that is, the quantum analogue of an angle between state "rays" (remembering that overall phase is unphysical) —the "angle" between two orthogonal states comes out as 90° (or \($\pi/2$\) radians) . In this metric:
```math
\text{Distance}(|\psi\rangle, |\phi\rangle)  = \arccos\left(|\langle \psi | \phi \rangle|\right) .
```
For \($|0\rangle$\) and \($|1\rangle$\),  
```math
\arccos(|\langle 0 | 1 \rangle|)  = \arccos(0)  = \frac{\pi}{2} \quad (\text{or 90°}) .
```

---

### 2. **From Hilbert Space to the Bloch Sphere**

When we represent a qubit on the Bloch sphere, we write a general state as:
```math
|\psi\rangle = \cos\left(\frac{\theta}{2}\right) |0\rangle + e^{i\phi}\sin\left(\frac{\theta}{2}\right) |1\rangle,
```
where:
- \($\theta$\) is the polar angle (\($0 \leq \theta \leq \pi$\)) ,
- \($\phi$\) is the azimuthal angle (\($0 \leq \phi < 2\pi$\)) .

Notice that the angle in the quantum state is \($\theta/2$\). This "half-angle" parameterization is crucial.  
- For \($|0\rangle$\), we set \($\theta = 0$\):  
```math
|\psi\rangle = \cos(0) |0\rangle + e^{i\phi}\sin(0) |1\rangle = |0\rangle.
```
- For \($|1\rangle$\), we set \($\theta = \pi$\):  
```math
|\psi\rangle = \cos\left(\frac{\pi}{2}\right) |0\rangle + e^{i\phi}\sin\left(\frac{\pi}{2}\right) |1\rangle = e^{i\phi}|1\rangle.
```

Since a global phase is irrelevant, \($|0\rangle$\) and \($|1\rangle$\) are mapped to the Bloch sphere in the following way:
- \($|0\rangle$\) corresponds to \($(0, 0, +1) $\) (the North Pole) .
- \($|1\rangle$\) corresponds to \($(0, 0, -1) $\) (the South Pole) .

The Euclidean angle between the North and South Poles (i.e., between \($(0, 0, +1) $\) and \($(0, 0, -1) $\))  is 180°.

---

### 3. **Understanding the Factor of Two**

The seeming mismatch—that orthogonal states in Hilbert space (90° by the Fubini–Study metric)  are represented as points 180° apart on the Bloch sphere—is resolved by realizing that the Bloch sphere has been constructed via a mapping that “doubles” the effective angle:

- **Fubini–Study Angle (Hilbert Space) :**  
  For orthogonal states, \($\arccos(0)  = \pi/2$\) (90°) .  
- **Bloch Sphere Angle (Geometric Representation) :**  
  Through the mapping \($\theta \to \theta/2$\) for state coefficients, the geometric vector corresponding to the state \($|\psi\rangle$\) is  
```math
\mathbf{r} = (\sin\theta\cos\phi,\; \sin\theta\sin\phi,\; \cos\theta) .
```
  Hence, \($|0\rangle$\) (with \($\theta = 0$\))  is at \($\mathbf{r} = (0,0,1) $\), and \($|1\rangle$\) (with \($\theta = \pi$\))  is at \($\mathbf{r} = (0,0,-1) $\). Their separation in \($\mathbb{R}^3$\) is  
```math
\cos^{-1}[(0,0,1) \cdot(0,0,-1) ] = \cos^{-1}(-1)  = \pi \quad (180^\circ) .
```

This doubling reflects the fact that the group of unitary operations on a qubit, SU(2) , is a double cover of the rotation group SO(3) . In simple terms, two distinct points on the Bloch sphere (separated by 180°)  actually represent quantum states that are 90° apart in the underlying Hilbert space metric.

---

### 4. **ASCII Diagram for Clarity**

```
               (0,0,1) 
                  |   <-- |0⟩ (North Pole) 
                  |
                  |        Bloch Vector
                  |
   -------------- • --------------   <-- Equator (θ = π/2) 
                 / \
                /   \
(0,0,-1)        /     \      (0,0,-1) 
   |         /         \        |  
   |   <-- |1⟩ (South Pole)  -->
```

- On the Bloch sphere, the two basis states are shown at the poles (180° apart) .
- The mapping from the Hilbert space uses a half-angle so that the Hilbert space “angle” between these states remains 90°.

---

### **Summary**

- **Hilbert Space:** Orthonormal states have a Fubini–Study angle of 90°.
- **Bloch Sphere:** The same states are mapped to antipodal points, which are 180° apart in Euclidean space.
- **Why the Difference?** This comes from the half-angle parameterization in the qubit state and the double-cover property of SU(2)  over SO(3) .

---

#### why do we represent a qubit general state on the Bloch sphere 1. in terms of cosine and sine. what is the intuition behind it 2. and how did we come to that formula?

Let's break down the answer into two parts:

---

### 1. Why Represent a Qubit in Terms of Cosine and Sine—the Intuition

A general qubit state is essentially a two-dimensional complex vector subject to the normalization condition. Conventionally, we write it as

```math
|\psi\rangle = \alpha|0\rangle + \beta|1\rangle,
```

with the condition

```math
|\alpha|^2 + |\beta|^2 = 1.
```

Because every complex number can be described in a polar form, we can express the amplitudes in a way that automatically satisfies this normalization. The standard choice is:

```math
\alpha = \cos\left(\frac{\theta}{2}\right) 
```
```math
\beta = e^{i\phi}\sin\left(\frac{\theta}{2}\right) ,
```

yielding

```math
|\psi\rangle = \cos\left(\frac{\theta}{2}\right) |0\rangle + e^{i\phi}\sin\left(\frac{\theta}{2}\right) |1\rangle.
```

**So why cosine and sine?**

- **Normalization Made Easy:** Notice that by using cosine and sine, we automatically meet the requirement:  
```math
\cos^2\left(\frac{\theta}{2}\right)  + \sin^2\left(\frac{\theta}{2}\right)  = 1.
```
  This mirrors the classic trigonometric identity for angles on a unit circle, where every point has coordinates defined by cosine and sine. 

- **Mapping to a Sphere:** In the Bloch sphere representation, a qubit’s state is visualized as a point on the surface of a unit sphere. In this geometric picture, \($\theta$\) and \($\phi$\) become the spherical coordinate angles—\($\theta$\) (the polar angle)  and \($\phi$\) (the azimuthal angle) . The use of cosine and sine is simply analogous to how we parameterize points on a circle or sphere in classical geometry.

- **Relative Amplitudes as Geometric Coordinates:**  
  - \($\cos\left(\frac{\theta}{2}\right) $\) determines the "weight" of the state \($|0\rangle$\), and  
  - \($\sin\left(\frac{\theta}{2}\right) $\) (together with the phase \($e^{i\phi}$\))  determines the "weight" and relative phase of the state \($|1\rangle$\).  
  The half-angle \($\theta/2$\) is chosen because it connects the geometry of the qubit’s Hilbert space (where rotations in the state vector are twice as “sensitive” as rotations on the sphere)  to the Bloch sphere’s angles.

In summary, cosine and sine naturally arise because they provide a smooth, normalized parameterization that fits both the requirements of quantum mechanics and the geometry of a sphere.

---

### 2. How Did We Arrive at This Formula?

The derivation of the Bloch sphere parameterization starts with the general requirements of a qubit:

1. **Two Complex Amplitudes:**  
   A qubit is a vector in a two-dimensional complex Hilbert space, so it must have two complex numbers \($\alpha$\) and \($\beta$\).

2. **Normalization:**  
   The amplitudes must satisfy \($|\alpha|^2 + |\beta|^2 = 1$\).

3. **Global Phase Invariance:**  
   Multiplying the entire state by a global phase (a complex number of magnitude 1)  does not affect any physical properties. This redundancy allows us to fix one of the amplitudes to be real and non-negative.

Given these points:
- One can choose a representation where the amplitude for \($|0\rangle$\) is real and positive, written as  
```math
\alpha = \cos\left(\frac{\theta}{2}\right) .
```
- The remaining complex amplitude is expressed with a magnitude and a phase. Its magnitude must satisfy \($\sin\left(\frac{\theta}{2}\right) $\) so that together with \($\alpha$\) the normalization holds; its phase is arbitrary and represented by \($e^{i\phi}$\):
```math
\beta = e^{i\phi}\sin\left(\frac{\theta}{2}\right) .
```

4. **Link to Spherical Coordinates:**  
   Notice that now we have two free parameters, \($\theta$\) and \($\phi$\), which are exactly the spherical coordinates needed to specify a point on the surface of a sphere (the Bloch sphere) . The factor of \($1/2$\) in the angles accounts for the fact that a full rotation in the state’s Hilbert space corresponds to a 360° change only when mapped appropriately onto a sphere. This mapping is deeply connected to the mathematics of the SU(2)  group (which describes qubit operations)  being a double cover of the SO(3)  rotation group.

5. **Historical and Mathematical Roots:**  
   When quantum mechanics was being formalized, it quickly became apparent that the space of pure states (ignoring global phase)  of a two-level system is isomorphic to the complex projective line, denoted \($ \mathbb{C}P^1 $\), which is topologically equivalent to a sphere. Parameterizing this with \($\theta$\) and \($\phi$\) (and hence using sine and cosine)  emerged as the natural and elegant choice.

---

### Bringing It All Together

The formula

```math
|\psi\rangle = \cos\left(\frac{\theta}{2}\right) |0\rangle + e^{i\phi}\sin\left(\frac{\theta}{2}\right) |1\rangle
```

is not arbitrary—it is the result of:

- **Enforcing normalization automatically** through the well-known identity \($\cos^2(\cdot)  + \sin^2(\cdot)  = 1$\).
- **Capturing the degrees of freedom** of a qubit (after discounting the irrelevant global phase)  exactly using two angles.
- **Connecting the algebra of the qubit’s state space (SU(2) )  to a geometric picture (the surface of a sphere, or the Bloch sphere) **, which is invaluable for visualizing and understanding the effects of quantum operations like rotations.

This representation has become fundamental because it bridges abstract quantum mechanics with intuitive geometric visualization.

---

The Bloch sphere is a fascinating representation of qubit states! To address your question, if we imagine the Bloch sphere divided into 8 quadrants, the task is to find the qubit states (pure states) within each quadrant that are at an angle of 45° with the \( $z$ \)-axis.

### Steps to find these qubit states:
1. **Understanding the coordinates on the Bloch sphere:**
   - Any pure state of a qubit can be represented on the Bloch sphere using spherical coordinates: 
     - Angle \( $\theta$ \): measures the angle from the \( $z$ \)-axis (runs from \( $0$ \) to \( $\pi$ \)).
     - Angle \( $\phi$ \): measures the angle in the \( $xy$ \)-plane (runs from \( $0$ \) to \( $2\pi$ \)).

2. **Condition for the angle \( $45^\circ$ \) with the \( $z$ \)-axis:**
   - The angle \( $\theta = \frac{\pi}{4}$ \) (in radians, 45° in degrees).
   - For this angle, the general state on the Bloch sphere can be expressed as:
  ```math
  \lvert \psi \rangle = \cos\left(\frac{\pi}{8}\right) \lvert 0 \rangle + e^{i\phi} \sin\left(\frac{\pi}{8}\right) \lvert 1 \rangle
  ```
   where \( $\phi$ \) varies.

3. **Assigning qubits to 8 quadrants:**
   - Divide the sphere into 8 equal quadrants by splitting the ranges of \( $\phi$ \) and the \( $x, y, z$ \)-axes.
   - Each quadrant will have a unique range of \( $\phi$ \):
     - Quadrant 1: \( $0 \leq \phi < \frac{\pi}{2}$ \)
     - Quadrant 2: \( $\frac{\pi}{2} \leq \phi < \pi$ \)
     - Quadrant 3: \( $\pi \leq \phi < \frac{3\pi}{2}$ \)
     - Quadrant 4: \( $\frac{3\pi}{2} \leq \phi < 2\pi$ \)
     - Similarly, for the other octants, include combinations of \( $\theta$ \) ranges.

4. **Result:**
   In each quadrant, a representative state will look like:
```math
\lvert \psi_{qk} \rangle = \cos\left(\frac{\pi}{8}\right) \lvert 0 \rangle + e^{i \phi_k} \sin\left(\frac{\pi}{8}\right) \lvert 1 \rangle
```
   where \( $\phi_k$ \) is the specific angle for that quadrant, taking into account the angular ranges for \( $\phi$ \) and the octants.

---

#### Upper hemisphere qubits

The quantum states you described on the Bloch sphere can be represented in matrix form. Let's construct the state vectors for the qubits that lie at \( $\theta = 45^\circ (\frac{\pi}{4})$ \) with the \( $z$ \)-axis in each quadrant of the Bloch sphere.

### General Pure State
The general state of a qubit at \( $\theta = \frac{\pi}{4}$ \) (45°) can be written as:
```math
\lvert \psi \rangle = \cos\left(\frac{\pi}{8}\right) \lvert 0 \rangle + e^{i\phi} \sin\left(\frac{\pi}{8}\right) \lvert 1 \rangle.
```
In matrix form:
```math
\lvert \psi \rangle =
\begin{bmatrix}
\cos\left(\frac{\pi}{8}\right) \\
e^{i\phi} \sin\left(\frac{\pi}{8}\right)
\end{bmatrix}.
```

### Finding Matrices for Each Quadrant
To specify the states in each quadrant, we need unique values of \( $\phi$ \) within the ranges corresponding to each quadrant. Here are the resulting matrices:

1. **Quadrant 1** (\( $0 \leq \phi < \frac{\pi}{2}$ \)):
```math
\lvert \psi_1 \rangle =
\begin{bmatrix}
\cos\left(\frac{\pi}{8}\right) \\
e^{i\cdot 0} \sin\left(\frac{\pi}{8}\right)
\end{bmatrix}.
=
\begin{bmatrix}
\cos\left(\frac{\pi}{8}\right) \\
\sin\left(\frac{\pi}{8}\right)
\end{bmatrix}.
```

2. **Quadrant 2** (\( $\frac{\pi}{2} \leq \phi < \pi$ \)):
```math
\lvert \psi_2 \rangle =
\begin{bmatrix}
\cos\left(\frac{\pi}{8}\right) \\
e^{i\frac{\pi}{2}} \sin\left(\frac{\pi}{8}\right)
\end{bmatrix}.
=
\begin{bmatrix}
\cos\left(\frac{\pi}{8}\right) \\
i \sin\left(\frac{\pi}{8}\right)
\end{bmatrix}.
```

3. **Quadrant 3** (\( $\pi \leq \phi < \frac{3\pi}{2}$ \)):
```math
\lvert \psi_3 \rangle =
\begin{bmatrix}
\cos\left(\frac{\pi}{8}\right) \\
e^{i\pi} \sin\left(\frac{\pi}{8}\right)
\end{bmatrix}.
=
\begin{bmatrix}
\cos\left(\frac{\pi}{8}\right) \\
-\sin\left(\frac{\pi}{8}\right)
\end{bmatrix}.
```

4. **Quadrant 4** (\( $\frac{3\pi}{2} \leq \phi < 2\pi$ \)):
```math
\lvert \psi_4 \rangle =
\begin{bmatrix}
\cos\left(\frac{\pi}{8}\right) \\
e^{i\frac{3\pi}{2}} \sin\left(\frac{\pi}{8}\right)
\end{bmatrix}.
=
\begin{bmatrix}
\cos\left(\frac{\pi}{8}\right) \\
-i \sin\left(\frac{\pi}{8}\right)
\end{bmatrix}.
```

For the 8 divisions (octants), we can further subdivide these states by assigning ranges of \( $\phi$ \) and adjust the phase accordingly.

#### Lower hemisphere qubits 

To find the states in the **lower hemisphere** of the Bloch sphere corresponding to \( $\theta = \frac{3\pi}{4}$ \) (135°, which places the qubits below the equator), we will use the same approach as before but with this new angle. The general formula for the state vector remains the same.

### General Pure State in the Lower Hemisphere
For \( $\theta = \frac{3\pi}{4}$ \), the general qubit state becomes:
```math
\lvert \psi \rangle = \cos\left(\frac{3\pi}{8}\right) \lvert 0 \rangle + e^{i\phi} \sin\left(\frac{3\pi}{8}\right) \lvert 1 \rangle.
```

Now, let's find specific states in the 4 quadrants of the lower hemisphere:

---

1. **Quadrant 5** (Corresponding to \( $0 \leq \phi < \frac{\pi}{2}$ \)):
```math
\lvert \psi_5 \rangle =
\begin{bmatrix}
\cos\left(\frac{3\pi}{8}\right) \\
e^{i\cdot 0} \sin\left(\frac{3\pi}{8}\right)
\end{bmatrix}
=
\begin{bmatrix}
\cos\left(\frac{3\pi}{8}\right) \\
\sin\left(\frac{3\pi}{8}\right)
\end{bmatrix}.
```

2. **Quadrant 6** (Corresponding to \( $\frac{\pi}{2} \leq \phi < \pi$ \)):
```math
\lvert \psi_6 \rangle =
\begin{bmatrix}
\cos\left(\frac{3\pi}{8}\right) \\
e^{i\frac{\pi}{2}} \sin\left(\frac{3\pi}{8}\right)
\end{bmatrix}
=
\begin{bmatrix}
\cos\left(\frac{3\pi}{8}\right) \\
i\sin\left(\frac{3\pi}{8}\right)
\end{bmatrix}.
```

3. **Quadrant 7** (Corresponding to \( $\pi \leq \phi < \frac{3\pi}{2}$ \)):
```math
\lvert \psi_7 \rangle =
\begin{bmatrix}
\cos\left(\frac{3\pi}{8}\right) \\
e^{i\pi} \sin\left(\frac{3\pi}{8}\right)
\end{bmatrix}
=
\begin{bmatrix}
\cos\left(\frac{3\pi}{8}\right) \\
-\sin\left(\frac{3\pi}{8}\right)
\end{bmatrix}.
```

4. **Quadrant 8** (Corresponding to \( $\frac{3\pi}{2} \leq \phi < 2\pi$ \)):
```math
\lvert \psi_8 \rangle =
\begin{bmatrix}
\cos\left(\frac{3\pi}{8}\right) \\
e^{i\frac{3\pi}{2}} \sin\left(\frac{3\pi}{8}\right)
\end{bmatrix}
=
\begin{bmatrix}
\cos\left(\frac{3\pi}{8}\right) \\
-i\sin\left(\frac{3\pi}{8}\right)
\end{bmatrix}.
```

---

### Recap
- The 4 states derived above correspond to the **lower hemisphere**, complementing the 4 states in the **upper hemisphere**.
- Together, these 8 states span the Bloch sphere at \( $\theta = \frac{\pi}{4}$ \) (upper) and \( $\theta = \frac{3\pi}{4}$ \) (lower), each at distinct quadrants defined by \( $\phi$ \).

