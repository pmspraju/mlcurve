---
title: Score Distillation Sampling
domain: ml
topic: cv
tags:
   - sds
   - diffusion
   - 3d-generation
updated: 2026-06-02
---

Let's dive deep into Score Distillation Sampling (SDS), a key technique introduced (for example, in DreamFusion) to distill the rich, text-conditioned knowledge of a pre-trained diffusion model into another model—in many cases, a 3D generator like a NeRF—even without explicit 3D supervision.

Below is a step-by-step explanation of SDS and the math behind it.

---

## 1. Core Idea

In many text-to-image diffusion models, the network is trained to predict added noise from a noised image. In standard diffusion training, one perturbs an image, and the model learns a mapping from a noisy version back to the original signal. SDS repurposes this idea to guide a separate model (say, a neural 3D scene representation) so that its rendered images are likely under the distribution learned by the diffusion model.

Rather than directly optimizing the rendered image’s likelihood under the diffusion prior—which is usually intractable—we compute a “score” signal:
```math
\nabla_{\mathbf{I}} \log p(\mathbf{I}\mid \mathbf{y}),
```
where:
- \( $\mathbf{I}$ \) is the rendered image (for instance, from a NeRF), and  
- \( $\mathbf{y}$ \) is a text prompt or conditioning information.

By leveraging the pretrained diffusion model as a fixed, differentiable “oracle,” we can compute gradients with respect to the input image. These gradients (or “score estimates”) then backpropagate all the way to the 3D model parameters. In essence, SDS *distills* the diffusion model’s understanding of what makes an image match a given prompt into the 3D generator.

---

## 2. Mathematical Foundations

### 2.1 Diffusion Models and Score Matching

In diffusion models one typically defines a forward process that progressively corrupts an image \( $\mathbf{I}_0$ \) into a noisy image \( $\mathbf{I}_t$ \) at time \( $t$ \) using a known noise schedule. A common reparameterization is:
```math
\mathbf{I}_t = \sqrt{\bar{\alpha}_t}\,\mathbf{I}_0 + \sqrt{1-\bar{\alpha}_t}\,\boldsymbol{\epsilon}, \quad \boldsymbol{\epsilon} \sim \mathcal{N}(0,\mathbf{I})
```
where
- \( $\bar{\alpha}_t$ \) is a cumulative noise coefficient (depending on the schedule), and  
- \( $\boldsymbol{\epsilon}$ \) is drawn from a standard Gaussian distribution.

The diffusion (denoising) network \( $\epsilon_\theta(\cdot)$ \) is trained to predict the noise \( $\boldsymbol{\epsilon}$ \) given the noisy image \( $\mathbf{I}_t$ \), time \( $t$ \), and optionally, conditioning signal \( $\mathbf{y}$ \). Its training loss is typically:
```math
\mathcal{L}_{\text{diff}} = \mathbb{E}_{t,\mathbf{I}_0,\boldsymbol{\epsilon}}\Bigl[\lambda(t)\,\bigl\|\epsilon_\theta\bigl(\mathbf{I}_t,t,\mathbf{y}\bigr)-\boldsymbol{\epsilon}\bigr\|^2\Bigr],
```
where \( $\lambda(t)$ \) is a weight that may depend on the noise level.

Importantly, under score matching theory, the network’s prediction connects to the score (the gradient of the log probability) approximately by:
```math
\nabla_{\mathbf{I}} \log p(\mathbf{I}\mid \mathbf{y}) \approx -\frac{1}{\sqrt{1-\bar{\alpha}_t}}\Bigl(\epsilon_\theta(\mathbf{I}_t,t,\mathbf{y})-\boldsymbol{\epsilon}\Bigr).
```
This expression tells us how to nudge an image in the direction of higher likelihood under the learned distribution.

---

### 2.2 The SDS Loss Formulation

When applying SDS to a 3D model, the overall goal is to adjust the 3D parameters \( $\theta$ \) so that the rendered image \( $\mathbf{I} = f_{\theta}(\text{scene})$ \) will have a high conditional probability \( $p(\mathbf{I}\mid \mathbf{y})$ \) under the diffusion model. However, rather than optimizing that likelihood directly, SDS uses the score from the diffusion model as a distillation signal.

**Step-by-step process:**

1. **Render an Image:**  
   Generate an image \( $\mathbf{I}$ \) from your current 3D model (e.g., via volumetric rendering in NeRF).

2. **Sample a Random Time and Noise:**  
   Choose a time \( $t$ \) from the noise schedule (often uniformly) and sample a Gaussian noise vector \( $\boldsymbol{\epsilon}$ \).

3. **Create a Noisy Version of the Rendered Image:**  
   Form the noised image
```math
\mathbf{I}_t = \sqrt{\bar{\alpha}_t}\,\mathbf{I} + \sqrt{1-\bar{\alpha}_t}\,\boldsymbol{\epsilon}.
```

4. **Obtain the Diffusion Model’s Prediction:**  
   Feed \( $\mathbf{I}_t$ \), \( $t$ \), and text prompt \( $\mathbf{y}$ \) into the pretrained diffusion network:
```math
\hat{\boldsymbol{\epsilon}} = \epsilon_\theta\bigl(\mathbf{I}_t,t,\mathbf{y}\bigr).
```

5. **Compute the SDS Loss:**  
   The loss is computed as the weighted squared error between the diffusion model’s predicted noise and the actual noise:
```math
\mathcal{L}_{\text{SDS}} = w(t) \,\bigl\|\hat{\boldsymbol{\epsilon}} - \boldsymbol{\epsilon}\bigr\|^2,
```
   where \( $w(t)$ \) is a weight derived from the noise level (for example, proportional to \( $1/\sqrt{1-\bar{\alpha}_t}$ \) or adapted to ensure proper scaling).

6. **Backpropagate via the Rendering Pipeline:**  
   Since the rendered image \( $\mathbf{I}$ \) is differentiable with respect to the 3D model’s parameters, the gradient of \( $\mathcal{L}_{\text{SDS}}$ \) can be chained back:
```math
\frac{\partial \mathcal{L}_{\text{SDS}}}{\partial \theta} = \frac{\partial \mathcal{L}_{\text{SDS}}}{\partial \mathbf{I}} \cdot \frac{\partial \mathbf{I}}{\partial \theta}.
```
   This gradient update nudges the 3D scene so that, when rendered, its images become more “in line” with what the diffusion model considers likely for the given text prompt.

---

## 3. Intuition and Insights

- **Distilling a 2D Prior into 3D:**  
  The diffusion model has learned a rich distribution over 2D images conditioned on text. SDS transfers that knowledge to a 3D representation without having any direct 3D supervision. The rendered images are effectively pushed toward regions of high probability in the 2D diffusion model’s learned space.

- **Gradient Signal Through the Score:**  
  The term \( $\hat{\boldsymbol{\epsilon}} - \boldsymbol{\epsilon}$ \) forms an proxy for the score:
```math
\nabla_{\mathbf{I}} \log p(\mathbf{I}\mid \mathbf{y}) \approx -\frac{1}{\sqrt{1-\bar{\alpha}_t}}\left(\hat{\boldsymbol{\epsilon}} - \boldsymbol{\epsilon}\right).
```
  This means the 3D model is updated in the direction that increases the log probability of its renderings under the diffusion model.

- **Weighting by Noise Level:**  
  The scale factor \( $w(t)$ \) ensures that samples from different noise levels are balanced appropriately. At high noise levels, the diffusion model’s predictions are less precise, so the gradients may be scaled differently compared to low-noise regimes.

---

## 4. An ASCII Flowchart of SDS

Below is an ASCII diagram that outlines the SDS process:

```
           ┌────────────────────────────┐
           │  Rendered Image I = fθ()   │
           └────────────────────────────┘
                        │
                        ▼
           ┌────────────────────────────┐
           │ Sample t (noise level) and │
           │ Gaussian noise ε         │
           └────────────────────────────┘
                        │
                        ▼
           ┌────────────────────────────┐
           │ Compute I_t =               │
           │ √ᾱₜ · I + √(1-ᾱₜ) · ε     │
           └────────────────────────────┘
                        │
                        ▼
           ┌────────────────────────────┐
           │ Diffusion Model:            │
           │ ε̂ = εθ(I_t, t, y)            │
           └────────────────────────────┘
                        │
                        ▼
           ┌────────────────────────────┐
           │ Compute SDS Loss:           │
           │ L_SDS = w(t) · ||ε̂ - ε||²    │
           └────────────────────────────┘
                        │
                        ▼
           ┌────────────────────────────┐
           │ Backpropagate through I     │
           │ to update θ:  ∂I/∂θ         │
           └────────────────────────────┘
```

---

## 5. Summary

- **Score Distillation Sampling (SDS)** leverages the power of a pretrained, text-conditioned diffusion model by using its estimated score (or denoising signal) to guide a separate 3D generator.
- The process begins by rendering an image from the 3D model, corrupting it with a known noise level, and then passing it through the diffusion model.
- The difference between the predicted noise and the actual injected noise acts as a proxy for the gradient of the log-likelihood, which is then used to update the 3D model.
- Mathematically, SDS is summarized by a loss term of the form
```math
\mathcal{L}_{\text{SDS}} = w(t)\,\bigl\|\epsilon_\theta\bigl(\mathbf{I}_t,t,\mathbf{y}\bigr) - \boldsymbol{\epsilon}\bigr\|^2,
```
  with gradients flowing via the rendering process back to the 3D parameters.

This technique elegantly distills 2D image priors into a 3D representation and has proven to be a powerful tool for tasks such as text-to-3D synthesis.

---

There’s plenty more to explore. For instance, one might consider:
- How different noise schedules and weighting functions \( $w(t)$ \) affect convergence.
- How the quality of the pretrained diffusion model influences the final 3D output.
- Ways to extend SDS to handle more complex conditioning (such as multi-view consistency or lighting changes).
