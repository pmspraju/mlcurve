---
title: Grover's Algorithm Overview
domain: qc
topic: algorithms
tags:
  - grover
  - search
  - quantum-algorithms
updated: 2026-06-02
---

Grover's algorithm gives a quadratic speedup for unstructured search.

At a high level:

- Start in uniform superposition.
- Apply oracle to mark target states.
- Apply diffusion operator to amplify marked amplitudes.
- Repeat about square-root of N iterations.

It is not exponential speedup, but it is a canonical example of amplitude amplification.
