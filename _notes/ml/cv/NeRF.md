---
title: NeRF
domain: ml
topic: cv
tags:
      - nerf
      - 3d-vision
      - rendering
updated: 2026-06-02
---

Let's take a detailed journey into Neural Radiance Fields (NeRF)—both at the conceptual and mathematical level. NeRF was introduced as a way to represent a 3D scene *continuously* using a neural network. Instead of relying on discrete representations like voxels or triangles, NeRF encodes a scene into the parameters of a multilayer perceptron (MLP) and uses ideas from volumetric rendering to reproduce high-quality images from novel viewpoints.

---

## 1. **Core Concept**

At its heart, NeRF learns a continuous function
```math
f: (\mathbf{x}, \mathbf{d}) \rightarrow (\sigma, \mathbf{c})
```
where:

- \( $\mathbf{x} = (x,y,z)$ \) is a point in 3D space.
- \( $\mathbf{d}$ \) is the viewing direction (usually parameterized by angles like \( $(\theta, \phi)$ \)).
- \( $\sigma$ \) is the volume density at \( $\mathbf{x}$ \) (think of this as how “opaque” or “dense” the point is).
- \( $\mathbf{c}$ \) represents the color (RGB) emitted from that point in the direction \( $\mathbf{d}$ \).

The goal is to recover the appearance and geometry of a scene from a set of 2D images with known camera poses.

---

## 2. **Volume Rendering Framework**

### **2.1 The Rendering Equation**

To compute the color of a pixel corresponding to a camera ray, NeRF uses a differentiable volume rendering formulation. Consider a ray:
```math
\mathbf{r}(t) = \mathbf{o} + t \mathbf{d},
```
where \( $\mathbf{o}$ \) is the camera origin, and \( $\mathbf{d}$ \) is the ray’s direction. The color \( $C(\mathbf{r})$ \) seen along this ray is given by integrating the contributions of all points along the ray:
```math
C(\mathbf{r}) = \int_{t_n}^{t_f} T(t) \, \sigma(\mathbf{r}(t)) \, \mathbf{c}(\mathbf{r}(t), \mathbf{d}) \, dt.
```
Here, the *transmittance* \( $T(t)$ \) is defined as
```math
T(t) = \exp\left(-\int_{t_n}^{t} \sigma(\mathbf{r}(s)) \, ds\right),
```
which represents the probability that light travels from the camera to \( $t$ \) without being absorbed.

### **2.2 Discretization**

Because exact integration is intractable, NeRF approximates the integral by sampling points along the ray:
1. **Divide the interval** \( $[t_n, t_f]$ \) into \( $N$ \) segments with sample positions \( $t_1, t_2, \ldots, t_N$ \).  
2. **Compute associated distances** \( $\delta_i = t_{i+1} - t_i$ \).

At each sample \( $i$ \), the network predicts:
- \( $\sigma_i = \sigma(\mathbf{r}(t_i))$ \),
- \( $\mathbf{c}_i = \mathbf{c}(\mathbf{r}(t_i), \mathbf{d})$ \).

Then the accumulated transmittance up to sample \( $i$ \) is approximated as:
```math
T_i = \exp\left(-\sum_{j=1}^{i-1} \sigma_j \, \delta_j\right),
```
and the final pixel color is computed as:
```math
\hat{C}(\mathbf{r}) \approx \sum_{i=1}^{N} T_i \, \left(1 - \exp(-\sigma_i \, \delta_i)\right) \, \mathbf{c}_i.
```
The term \( $1 - \exp(-\sigma_i\,\delta_i)$ \) represents the probability that the ray “terminates” at sample \( $i$ \) by interacting with some matter (i.e., being absorbed or scattered).

---

## 3. **The Neural Network Architecture**

The MLP in NeRF isn’t a plain black box—it’s carefully designed to handle spatial details and view-dependent effects.

### **3.1 Positional Encoding**

Raw 3D coordinates aren’t ideal for capturing high-frequency details. NeRF employs a positional encoding (also known as Fourier features) to map each coordinate into a higher-dimensional space:
```math
\gamma(p) = \left[\sin(2^0 \pi p), \cos(2^0 \pi p), \sin(2^1 \pi p), \cos(2^1 \pi p), \dots, \sin(2^{L-1} \pi p), \cos(2^{L-1} \pi p)\right]
```
For a 3D point \( $\mathbf{x}$ \), this encoding is applied to each coordinate separately and then concatenated. A similar encoding can be applied to the viewing direction \( $\mathbf{d}$ \).

### **3.2 Two-Stage MLP Structure**

A common design divides the process into two stages:
- **Geometry Network:** Processes the positional-encoded \( $\mathbf{x}$ \) to compute the density \( $\sigma$ \) and an intermediate feature vector.
- **Color Network:** Combines the intermediate features with the positional-encoded viewing direction \( $\mathbf{d}$ \) to output \( $\mathbf{c}$ \).

An ASCII diagram of the pipeline might look like:

```
           [Input: 3D point (x, y, z)]
                      |
            Positional Encoding
                      |
                MLP Layers (with skip connections)
                      |
        ┌----------------------------┐
        |  Outputs: Intermediate   |--> Density σ
        |  feature vector          |
        └----------------------------┘
                      |
           Concatenate with encoded viewing direction
                      |
                Additional MLP layers
                      |
                 Output: Color (RGB)
```

This separation helps the model first understand the static geometry of the scene and then refine the appearance based on the viewing direction (accounting for effects such as specular highlights).

---

## 4. **Hierarchical Sampling**

An essential innovation in NeRF is its two-stage sampling process:
1. **Coarse Sampling:** Uniformly sample points along each ray and use these samples to compute a coarse estimate of the volume density.
2. **Fine Sampling:** Use the outputs of the coarse network to guide importance sampling—focusing on intervals along the ray with higher density values. Then evaluate more samples in these "important" regions using a second, fine network.

This hierarchical approach ensures that computational resources concentrate on parts of the scene that contribute most to the final pixel color.

---

## 5. **Training and Optimization**

The entire rendering process—from sampling along rays to accumulating colors—is fully differentiable. This enables the use of gradient-based optimization. Given a set of training images with known camera poses, the loss function is typically a simple mean squared error between the rendered pixel colors and the ground-truth:
```math
\mathcal{L} = \frac{1}{N_{\text{rays}}} \sum_{\mathbf{r}} \left\|\hat{C}(\mathbf{r}) - C_{\text{gt}}(\mathbf{r})\right\|_2^2.
```
Both the coarse and fine networks are trained jointly by backpropagating this loss through the entire rasterization process. Because the network learns not only the scene's geometry but also view-dependent appearance, it produces highly realistic images even from novel viewpoints.

---

## 6. **Putting It All Together**

1. **Scene Representation:** The scene is represented as a continuous function \( $f(\mathbf{x}, \mathbf{d})$ \) using an MLP, with positional encodings facilitating the learning of high-frequency details.
2. **Ray Marching:** For each pixel, construct a ray and sample points along it.
3. **Volume Rendering:** Use the predicted density and color values from the MLP to integrate along the ray and compute the pixel color.
4. **Hierarchical Sampling:** Improve efficiency by first approximating where the important contributions lie and then refining the sampling in those regions.
5. **Optimization:** Train the network by minimizing the mean squared error between rendered images and actual photographs.

---

## 7. **Further Thoughts and Practical Considerations**

- **High-Frequency Details:** Positional encoding is crucial. Without it, the MLP struggles to recover fine details, resulting in blurry outputs.
- **View Dependence:** By incorporating the viewing direction, NeRF can capture specular and other view-dependent effects. This is a key step in achieving photorealism.
- **Computational Considerations:** Despite its impressive results, NeRF can be computationally intensive both in training (due to the need for many samples per ray) and in rendering.
- **Extensions:** Many follow-up works have extended NeRF to dynamic scenes, relighting, and more efficient architectures that reduce the computational overhead.

---

## **ASCII Flowchart of the NeRF Process**

```
      ┌─────────────────────────────────────┐
      │         Input Ray (r(t))            │
      │  (origin o and direction d)         │
      └─────────────────────────────────────┘
                   │
                   ▼
      ┌─────────────────────────────────────┐
      │  Stratified Sampling along the ray  │
      │   (get sample points: t_1, ..., t_N)  │
      └─────────────────────────────────────┘
                   │
                   ▼
      ┌─────────────────────────────────────┐
      │  Positional Encoding of (x, y, z)   │
      │  (and encoding for view direction)  │
      └─────────────────────────────────────┘
                   │
                   ▼
      ┌─────────────────────────────────────┐
      │    MLP (Geometry + Color Networks)  │
      │       - Outputs: σ and intermediate   │ 
      │         features, then RGB color      │
      └─────────────────────────────────────┘
                   │
                   ▼
      ┌─────────────────────────────────────┐
      │   Discrete Volume Rendering         │
      │   (Compute color by summing samples)│
      └─────────────────────────────────────┘
                   │
                   ▼
      ┌─────────────────────────────────────┐
      │   Loss Calculation (MSE with GT)    │
      └─────────────────────────────────────┘
                   │
                   ▼
      ┌─────────────────────────────────────┐
      │       Backpropagation & Optimization│
      └─────────────────────────────────────┘
```

---

## **Wrapping Up**

NeRF represents a fascinating blend of classical computer graphics (volume rendering) with modern deep learning (coordinate-based MLPs with positional encodings). By doing so, it allows a compact, continuous representation of complex scenes learned directly from images, enabling high-quality novel view synthesis.

There’s ample space to dive even deeper—for instance, exploring:
- The nuances of the importance sampling scheme and its benefits.
- How NeRF’s differentiability paves the way for end-to-end learning from sparse data.
- Comparisons between NeRF and other 3D reconstruction methods, exploring trade-offs between fidelity, speed, and expressiveness.
