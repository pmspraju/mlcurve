---
title: 09 Unitary
domain: qc
topic: basics
tags:
  - unitary
  - gates
  - evolution
updated: 2026-06-02
---

In quantum computing, **unitary transformations** are indispensable because they ensure that the fundamental postulates of quantum mechanics—especially the preservation of probability—remain valid during the evolution of quantum states. Let’s explore this in a detailed, step-by-step manner.

---

### 1. **Normalization and Probability Preservation**

A quantum state is usually represented by a vector $|\psi\rangle$ in a complex Hilbert space. This vector is **normalized** so that:

```math
\langle \psi | \psi \rangle = 1
```

This normalization implies that the total probability (interpreted as the square of the amplitude) of all measurement outcomes sums to 1. When we apply any transformation to the state, the new state must remain normalized to preserve this total probability. 

**Unitary operators** $U$ are defined such that:

```math
U^\dagger U = I
```

where $U^\dagger$ is the conjugate transpose of $U$, and $I$ is the identity operator. This property guarantees that for any state $|\psi\rangle$:

```math
\langle \psi | \psi \rangle = \langle U\psi | U\psi \rangle
```

In other words, unitary transformations **preserve the norm** (or length) of quantum state vectors. This preservation is crucial because the norm is directly linked to the probability amplitudes.

---

### 2. **Preserving the Inner Product**

The **inner product** between two quantum states $|\phi\rangle$ and $|\psi\rangle$ captures essential information about their relative phase and overlap, influencing interference effects.

- Given two states $|\psi\rangle$ and $|\phi\rangle$ in Hilbert space, their inner product is $\langle \phi | \psi \rangle$.

- If we apply a unitary transformation $U$ to both states, we have:

```math
\langle \phi | \psi \rangle \quad \rightarrow \quad \langle U\phi | U\psi \rangle = \langle \phi | U^\dagger U | \psi \rangle = \langle \phi | I | \psi \rangle = \langle \phi | \psi \rangle
```

Thus, **the inner product is invariant under unitary transformations.** This invariance is essential for two reasons:

1. **Interference Patterns:** Quantum algorithms often rely on the interference of amplitude probabilities. The constructive and destructive interference effects, which are foundational for speedups in quantum algorithms, depend critically on the relative phases (and thus the inner products) between states.

2. **Reproducibility of Measurements:** In quantum mechanics, the probability of transitioning between states (or the probability amplitude) is determined by the inner product. If this inner product weren’t preserved, measurement outcomes would be unpredictable or inconsistent with the theory’s requirements.

---

### 3. **Reversibility of Quantum Operations**

A fundamental tenet of quantum evolution (excluding the act of measurement) is that it is **reversible**. Every unitary operator has an inverse (its conjugate transpose, $U^\dagger$), ensuring that the transformation can be undone. This reversibility is key to:

- **Error Correction:** In quantum computing, the ability to reverse operations (or detect and correct errors) depends on preserving the full information of the quantum state.
- **Quantum Algorithm Design:** Many quantum algorithms require precise control and retracing of evolution steps. The unitary nature ensures that no information is “lost” during the process.

---

### 4. **Visualizing Unitary Transformations**

Here’s an ASCII flowchart that illustrates how a unitary operator $U$ acts on a quantum state while preserving normalization and the inner product:

```
          Initial Quantum State
                 |ψ⟩
              (Normalization)
            ⟨ψ|ψ⟩ = 1
                 |
            Apply U (Unitary)
                 |
         Transformed Quantum State
              |φ⟩ = U|ψ⟩
                 |
   Preservation of Norm: ⟨φ|φ⟩ = ⟨ψ|ψ⟩ = 1
```

This simple diagram encapsulates the notion that after the transformation, all the physical quantities tied to the state remain valid and consistent with quantum principles.

---

### 5. **Practical Examples in Quantum Gates**

Most quantum gates (the building blocks of quantum circuits) are unitary. For instance:

- **Pauli-X Gate:**  
```math
X = \begin{pmatrix} 0 & 1 \\ 1 & 0 \end{pmatrix}, \quad X^\dagger X = I
```

- **Hadamard Gate:**  
```math
H = \frac{1}{\sqrt{2}} \begin{pmatrix} 1 & 1 \\ 1 & -1 \end{pmatrix}, \quad H^\dagger H = I
```

These gates transform the qubit states while ensuring the total probability remains 1.

---

### **In Summary**

- **Unitary transformations** preserve both the **norm** and **inner product** of quantum states.
- This preservation is essential for **probability conservation**, which ensures the sum of all probabilities remains equal to 1.
- **Interference**—a key quantum phenomenon—is maintained because the relative phases (embedded in the inner product) are conserved.
- **Reversibility** of quantum evolution is guaranteed, allowing transformations to be undone, which is critical for reliable quantum computations.

Every quantum evolution (again, excluding measurement) must adhere to these unitary characteristics to ensure that the theory remains self-consistent and that the outcomes of quantum computations are reliable.

---

Let's explore quantum evolution through the lens of a concrete physical example. Imagine we have a quantum system—say, a photon with polarization states or an electron with spin states. In both cases, the quantum state is represented by a vector in a complex Hilbert space. The evolution of this state—from one configuration to another—is described by a **unitary operator**. Let’s delve into this step by step.

---

## 1. **Quantum States and Their Representations**

### **For a Photon (Polarization States)**

A photon might be in a superposition of two orthogonal polarization states, typically chosen as horizontal $|H\rangle$ and vertical $|V\rangle$. Its state can be written as:

```math
|\psi\rangle = \alpha |H\rangle + \beta |V\rangle \quad \text{with} \quad |\alpha|^2 + |\beta|^2 = 1.
```

### **For an Electron (Spin States)**

Consider an electron, which is a two-level quantum system regarding its spin. We might refer to spin-up $|\uparrow\rangle$ and spin-down $|\downarrow\rangle$ along a specific axis (say, the z-axis). The quantum state of the electron can similarly be expressed as:

```math
|\psi\rangle = c_{\uparrow} |\uparrow\rangle + c_{\downarrow} |\downarrow\rangle \quad \text{with} \quad |c_{\uparrow}|^2 + |c_{\downarrow}|^2 = 1.
```

In both examples, the normalization condition (the total probability equaling 1) is critical.

---

## 2. **Time Evolution via Unitary Operators**

In quantum mechanics, the time evolution of a closed system is governed by the Schrödinger equation. The formal solution to this equation can be expressed as an operator acting on the initial quantum state:

```math
|\psi(t)\rangle = U(t) |\psi(0)\rangle,
```

where $U(t)$ is the **unitary operator** given by:

```math
U(t) = \exp\left(-\frac{i}{\hbar} H t \right).
```

Here, $H$ is the time-independent Hamiltonian of the system, which is Hermitian by construction. The Hermiticity of $H$ guarantees that $U(t)$ is unitary, meaning:

```math
U^\dagger(t) U(t) = I.
```

This relation is what ensures both **norm preservation** and **inner product invariance**.

---

## 3. **Preservation of Probabilities and Inner Products**

### **Norm Preservation**

For any initial state $|\psi(0)\rangle$, the unitary evolution guarantees:

```math
\langle \psi(t) | \psi(t) \rangle = \langle \psi(0) | U^\dagger(t) U(t) | \psi(0) \rangle = \langle \psi(0) | \psi(0) \rangle = 1.
```

Since the squared modulus of the amplitude (or the norm squared) represents the probability distribution of outcomes, this ensures that the total probability remains always equal to 1.

### **Inner Product Preservation**

Consider two quantum states $|\psi\rangle$ and $|\phi\rangle$. Their inner product $\langle \phi | \psi \rangle$ contains vital phase information that determines how these states interfere—this is essential for quantum algorithms and experiments. Under a unitary evolution:

```math
\langle \phi(t) | \psi(t) \rangle = \langle \phi(0) | U^\dagger(t) U(t) | \psi(0) \rangle = \langle \phi(0) | \psi(0) \rangle.
```

The invariance of the inner product means that relative phases and interference properties are preserved. This has profound implications: interference (both constructive and destructive) will behave exactly as expected—a cornerstone of quantum phenomena.

---

## 4. **Physical Realizations of Unitary Evolution**

### **For a Photon: Role of Optical Components**

Imagine a photon passing through a half-wave plate. A half-wave plate acts as a specific unitary transformation on the photon's polarization state. If the input state is

```math
|\psi_{\text{in}}\rangle = \alpha |H\rangle + \beta |V\rangle,
```

after the half-wave plate, it might be transformed to:

```math
|\psi_{\text{out}}\rangle = \alpha' |H'\rangle + \beta' |V'\rangle,
```

where $|H'\rangle$ and $|V'\rangle$ are rotated polarization bases. The transformation $U_{\text{HWP}}$ satisfies:

```math
|\psi_{\text{out}}\rangle = U_{\text{HWP}}\,|\psi_{\text{in}}\rangle,
```

with $U_{\text{HWP}}^\dagger U_{\text{HWP}} = I$. This maintains the normalization $|\alpha'|^2 + |\beta'|^2 = 1$, ensuring that our photon’s probabilities sum to one.

### **For an Electron: Spin Precession**

Consider an electron in a magnetic field. The Hamiltonian for a spin-$\frac{1}{2}$ particle in a magnetic field $\vec{B}$ is given by:

```math
H = -\gamma \vec{B} \cdot \vec{\sigma},
```

where $\gamma$ is the gyromagnetic ratio and $\vec{\sigma}$ represents the Pauli matrices. The corresponding time evolution operator is:

```math
U(t) = \exp\left(i\gamma \vec{B} \cdot \vec{\sigma}\, t\, / \hbar \right).
```

This operator rotates the electron’s spin state on the Bloch sphere. If initially the electron is in the state $|\uparrow\rangle$ along the z-axis, after time $t$ its state might become a superposition of $|\uparrow\rangle$ and $|\downarrow\rangle$, but still obeying:

```math
|\psi(t)\rangle = U(t)|\psi(0)\rangle, \quad \langle \psi(t)|\psi(t) \rangle = 1.
```

The evolution is smooth, reversible, and entirely deterministic (until a measurement is made), with the transformation fully reversible by applying $U^\dagger(t)$.

---

## 5. **ASCII Diagram of Unitary Evolution**

Below is a simple flowchart that shows how a quantum state evolves under a unitary operator:

```
               Initial State at t = 0
                      │
         |ψ(0)⟩ (normalized: ⟨ψ(0)|ψ(0)⟩ = 1)
                      │
         Unitary Transformation U(t)
                      │
                      ▼
              Final State at time t
                 |ψ(t)⟩ = U(t)|ψ(0)⟩
                      │
            Norm Preserved: ⟨ψ(t)|ψ(t)⟩ = 1
```

This diagram emphasizes that while the precise composition (amplitude and phase) of the state vectors might change, the overall magnitude (and thus the probability interpretation) remains intact.

---

## 6. **Putting It All Together**

In summary, when we describe the evolution of a quantum system—whether it’s an electron’s spin state or a photon’s polarization state—we are referring to:

- **A Unit Bare Transformation:** $|\psi(t)\rangle = U(t)|\psi(0)\rangle$
- **Norm Preservation:** $\langle \psi(t)|\psi(t)\rangle = \langle \psi(0)|\psi(0)\rangle = 1$
- **Inner Product Invariance:** Ensuring that interference patterns (encoded in the phases and overlaps) do not get lost or distorted.

This unitary evolution is fundamental because it ensures that the quantum system evolves in a deterministic, reversible manner and that the probabilistic predictions of quantum mechanics remain consistent.

---

Let's connect the abstract algorithmic description with what happens in the lab. At the theory level, we model the evolution of the electron spin—or any two-level system—as a unitary rotation on the Bloch sphere. In hardware, this rotation is achieved by precise electromagnetic control. Let’s break down how this happens.

---

## 1. **The Experimental Setup**

### **Defining the Qubit:**
- **Electron Spin States:** In many hardware implementations (like quantum dots or defects in diamond), an electron’s spin serves as a qubit. The two orthogonal states, conventionally labeled as $|\uparrow\rangle$ (spin-up) and $|\downarrow\rangle$ (spin-down), form the computational basis.
  
### **Static Magnetic Field:**
- **Zeeman Splitting:** Typically, a strong, static magnetic field $B_0$ is applied along, say, the z-axis. This field defines a quantization axis and splits the energy levels of the spin states via the Zeeman effect:
```math
H_0 = -\gamma B_0 S_z,
```
  where $\gamma$ is the gyromagnetic ratio and $S_z$ is the spin operator along z.
- **Role in Hardware:** This constant field is generated by superconducting magnets or electromagnets and is crucial for setting the energy difference (and therefore the resonance frequency) between the two spin states.

---

## 2. **Driving the Rotation: The Oscillating Field**

### **Applying an RF/Microwave Pulse:**
- **Transverse Field:** To rotate the electron spin, we apply a second, time-dependent magnetic field $B_1$ that oscillates perpendicular to $B_0$. For example, this field can be directed along the x-axis or y-axis.
- **Resonance Condition:** The frequency $\omega$ of this oscillatory field is tuned to match the energy difference between the spin states. This is essentially what electron spin resonance (ESR) is all about:
```math
\hbar\omega = \Delta E = \gamma \hbar B_0.
```

### **Effective Hamiltonian with the Oscillatory Field:**
- The total Hamiltonian during the pulse is time-dependent. Under the rotating wave approximation (RWA), it simplifies to an effective Hamiltonian that looks like:
```math
H_{\text{eff}} = \frac{\hbar \Omega_R}{2}\,\sigma_x,
```
  where:
  - $\Omega_R$ is the Rabi frequency, proportional to the amplitude $B_1$ of the pulse,
  - $\sigma_x$ is the Pauli-X operator (if the pulse is applied along the x-axis).

---

## 3. **From Pulse to Unitary Rotation**

### **Rabi Oscillations and Pulse Duration:**
- **Rabi Oscillations:** Under $H_{\text{eff}}$, the electron spin oscillates between $|\uparrow\rangle$ and $|\downarrow\rangle$; these are known as Rabi oscillations.
- **Controlling the Rotation Angle:**  
  The angle of rotation $\theta$ on the Bloch sphere is given by:
```math
\theta = \Omega_R \, t,
```
  where $t$ is the duration the pulse is applied.
  
  - For a π-pulse ($\theta = \pi$), the state flips from $|\uparrow\rangle$ to $|\downarrow\rangle$.
  - For a π/2-pulse ($\theta = \pi/2$), the state rotates to an equal superposition.

### **Unitary Description in Hardware:**
- **Mathematical Mapping:** The pulse implements the unitary operator:
```math
U(\theta) = \exp\left(-i \frac{\theta}{2} \sigma_x \right).
```
  This operator rotates the electron spin on the Bloch sphere by $\theta$ around the x-axis.
  
- **Hardware Control:** The actual hardware—comprising signal generators, oscillators, and antennas or waveguides—must be tuned to provide:
  - **Precise Frequency:** Matching the electron's resonance condition.
  - **Controlled Amplitude:** Setting the Rabi frequency $\Omega_R$.
  - **Accurate Pulse Duration:** Timing the pulse to achieve the exact rotation angle.

---

## 4. **Practical Considerations in the Hardware**

### **Isolation & Coherence:**
- **Well-Isolated Environment:**  
  For the unitary rotation to be faithful (i.e., to avoid decoherence), the electron spin must be well isolated from the environment. Advanced cryogenic techniques and vacuum setups help in achieving this.

### **Pulse Shaping:**
- **Reducing Errors:**  
  Real-life pulses are rarely perfect square waves. Hardware often uses shaped pulses (Gaussian or composite pulses) to minimize errors like off-resonance effects or variations in field strength.

### **Calibration and Feedback:**
- **Calibration:**  
  Engineers calibrate the pulse parameters (amplitude, frequency, and duration) by monitoring the system's response (using techniques like Ramsey interferometry or spin echo measurements). This ensures that the actual rotation closely matches the theoretical unitary operation.
- **Feedback Loops:**  
  Active feedback is used to correct for drift and other imperfections, thus ensuring reproducibility and high-fidelity operations.

---

## 5. **Illustrative ASCII Diagram**

Below is an ASCII diagram that encapsulates the process:

```
             ┌─────────────────────────────┐
             │   Static Magnetic Field     │
             │        (B₀ along z)         │
             └─────────────────────────────┘
                           │
                           ▼
              Establishes Zeeman Splitting
                           │
                           ▼
            ┌─────────────────────────────┐
            │  Oscillatory RF/Microwave   │
            │         Pulse (B₁ along x)   │
            └─────────────────────────────┘
                           │
                           ▼
             Effective Hamiltonian H_eff
                           │
                           ▼
                    Controlled Rabi Oscillations
                           │     (θ = Ω_R t)
                           ▼
             ┌─────────────────────────────┐
             │  Unitary Rotation Operator  │
             │  U(θ) = exp(-iθσₓ/2)         │
             └─────────────────────────────┘
                           │
                           ▼
            Electron Spin State Rotated (Unitary Evolution)
```

---

## 6. **Synthesis: From Hardware to Algorithm**

In summary, while algorithmically we describe a spin rotation as a unitary operation $U = \exp(-i\theta\sigma/2)$, the hardware implements this by:

1. **Setting a Baseline with a Static Magnetic Field $B_0$** to create a well-defined two-level system (Zeeman splitting).
2. **Applying a Resonant RF/Microwave Pulse $B_1$** to induce controlled Rabi oscillations.
3. **Timing the Pulse Properly** so that the effective Hamiltonian rotates the spin state on the Bloch sphere by the desired angle $\theta$.

This is how the abstract concept of unitary rotation is physically realized in a laboratory setting, marrying theory with exquisite experimental control.

---

**Further Explorations:**  
- **Advanced Error Correction:** How hardware engineers design pulse sequences to counteract environmental noise.
- **Decoherence Mechanisms:** A detailed look at how interactions with the environment affect the ideal unitary evolution.
- **Other Qubit Implementations:** Comparing electron spin control with other systems like superconducting qubits or trapped ions, each with their own hardware nuances.

