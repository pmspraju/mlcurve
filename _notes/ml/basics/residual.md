---
title: Residual Blocks
domain: ml
topic: basics
tags:
        - residual
        - resnet
        - skip-connections
updated: 2026-06-02
---

## Residual blocks

### A residual block adds a "skip connection" that lets information bypass some layers in a neural network:

Key components:
1. Input splits into two paths
2. Main path: Goes through conv layers/activations
3. Skip path: Direct connection bypassing those layers
4. Paths merge via addition at the end

Benefits:
1. Prevents vanishing gradients in deep networks
2. Easier optimization since network can learn residual function
3. Better information flow through network

```
Input → Conv1 → BN → ReLU → Conv2 → BN → + → ReLU → Output
     ↘________________________________↗
        Skip Connection
```

This lets the network decide whether to use the transformed features or preserve input features.
Used extensively in modern architectures like ResNet, making training of very deep networks (100+ layers) feasible.

#### can you please explain the point easier optimization because network can learn residual function ?

Let's break it down with a simple analogy:
Imagine teaching someone to hit a target:

Without residual: They must learn the exact force and angle needed
With residual: They start at the target and learn how much to adjust from there

In neural networks:

Traditional: Network must learn the complete mapping H(x)
Residual: Network learns the difference F(x) = H(x) - x

It's like saying "learn how to modify the input" rather than "learn everything from scratch." This is typically an easier optimization problem since zero is often a good initial guess for the residual.
If no transformation is needed, the network can easily learn F(x) ≈ 0 by pushing weights close to zero.

#### so does it have significance when to skip and connect the input back?

The skip connection's significance depends on the layer's depth and task:
Early layers: Less skipping needed as they learn basic features
Deep layers: More important to skip as they:

Prevent gradient vanishing
Preserve low-level features needed for final prediction
Allow network to selectively use complex transformations

Example: In image recognition, early layers detect edges/textures, while deeper layers combine these into complex patterns. Skip connections ensure those basic features remain accessible.


