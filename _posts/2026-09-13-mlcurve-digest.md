---
title: "MLCurve Digest - 2026-09-13"
date: 2026-09-13 02:52:16 +0000
layout: post
source: mlcurve-digest
---

## TL;DR
- viserys-agent is gaining traction (626 stars, score 36.52).
- recurrent-looped-tranformer is gaining traction (172 stars, score 27.44).
- anything2explainer is gaining traction (1082 stars, score 25.64).
- dream-loop is gaining traction (924 stars, score 22.48).
- openai published Perplexity trusts GPT-6 Astra with end-to-end systems (score 50.0).

## Top Open Source Repos
1. [viserys-agent](https://github.com/rizqinrr/viserys-agent)

viserys-agent supplies a Python SDK that lets developers create and register extensions, then start, control, and communicate with local or remote AI engine instances via clear entry points for extension authors and engine clients. It matters now because it offers a lightweight, framework‑agnostic way to embed custom logic and manage LLM runtimes in reproducible, version‑controlled pipelines, addressing the growing need for modular, controllable agents in production AI/ML workflows.

_Source: ai-agents | Published: 2026-09-12T16:51:29+00:00 | Score: 36.52 | Stars: 626 | ✨ AI-enriched_

2. [recurrent-looped-tranformer](https://github.com/yifanzhang-pro/recurrent-looped-tranformer)

The Recurrent Looped Transformer (RLT) couples a causal encoder with a recurrent decoder that propagates its final hidden state and a layer‑wise sliding‑window attention cache across every prompt and response token, enabling a single recurrent computation to extend latent reasoning to unbounded temporal depth while sharing parameters between pre‑training, fine‑tuning, sampling and RL replay. It matters now because it offers a hardware‑efficient way to increase effective model depth and maintain consistent state across long‑context interactions, addressing the growing demand for scalable, compositional reasoning in modern LLM pipelines.

_Source: llm | Published: 2026-09-12T19:02:46+00:00 | Score: 27.44 | Stars: 172 | ✨ AI-enriched_

3. [anything2explainer](https://github.com/Vincentwei1021/anything2explainer)

It provides a Claude Code / Codex skill that turns a supplied topic into a black‑canvas motion‑graphics explainer video—rendered entirely with Remotion code—and adds TTS voiceover, subtitles, and a chapter progress bar in Chinese or English. For AI/ML practitioners, it delivers a fully automated, code‑driven way to produce polished tutorial or model‑explanation videos without manual design or stock footage, speeding up the sharing and documentation of complex agent concepts.

_Source: ai-agents | Published: 2026-09-08T17:19:54+00:00 | Score: 25.64 | Stars: 1082 | ✨ AI-enriched_

4. [dream-loop](https://github.com/achimala/dream-loop)

It provides an agent skill that closes a feedback loop between a text‑to‑image generator, Blender scene construction, and a fresh sub‑agent critic, iteratively rebuilding a 3D scene until the critic’s gated 0‑10 score meets a quality threshold. This matters now because it showcases a practical recipe for combining vision, generative, and evaluation models so AI/ML practitioners can automate high‑fidelity 3D asset creation for rapid prototyping, synthetic‑data pipelines, and game‑engine workflows.

_Source: ai-agents | Published: 2026-09-07T14:19:20+00:00 | Score: 22.48 | Stars: 924 | ✨ AI-enriched_


## Research and Company Updates
1. [Perplexity trusts GPT-6 Astra with end-to-end systems](https://openai.com/index/perplexity-improving-accuracy-with-astra)

Perplexity announced that it has deployed OpenAI’s GPT‑6 Astra model to draft communications, modify software, and monitor production systems, with the engineering team checking the model’s output far less frequently than with earlier generations. This marks a significant shift toward autonomous, AI‑driven DevOps workflows, offering efficiency gains but also raising important questions about safety, oversight, and reliability in live‑system operations.

_Source: openai | Published: 2026-09-14T00:00:00+00:00 | Score: 50.0 | ✨ AI-enriched_

2. [Cognition helps Devin test its own work with GPT‑6 Astra](https://openai.com/index/cognition-devin-testing-with-astra)

Cognition announced that its autonomous software engineer Devin now embeds OpenAI’s GPT‑6 Astra model to generate and execute tests on its own code, delivering simulator recordings and verification reports as evidence of functionality. By providing concrete test artifacts, the integration lets engineers review far less code, speeding up bug fixes and feature releases.

_Source: openai | Published: 2026-09-11T16:00:00+00:00 | Score: 40.0 | ✨ AI-enriched_

3. [Rapidly scaling online storage to serve over 1 billion ChatGPT users](https://openai.com/index/scaling-storage-one-billion-users-part-one)

OpenAI announced that its Habitat storage system has been re‑engineered from a modest Python library into a globally distributed platform that now supports over 1 billion ChatGPT users and handles roughly 22 million requests per second. This matters because the new architecture provides sub‑10 ms latency, fault‑isolated cells, and multi‑region availability, ensuring seamless, responsive interactions for a massive user base and showcasing the infrastructure scale required for consumer‑grade AI services.

_Source: openai | Published: 2026-09-11T10:00:00+00:00 | Score: 40.0 | ✨ AI-enriched_

4. [Skild AI Taps NVIDIA Physical AI to Teach Robots New Tasks From a Single Video](https://blogs.nvidia.com/blog/skild-ai-s1-physical-ai/)

Skild AI unveiled its S1 robot foundation model, which uses NVIDIA’s Physical AI stack (Isaac Lab, Cosmos, Omniverse) to let a robot learn a previously unseen, long‑horizon task from a single video demonstration via in‑context learning, without any weight updates or task‑specific retraining. This capability cuts weeks of data collection and reprogramming down to minutes, delivering a 66 % per‑step success rate on multistep tasks (versus ~9 % for comparable systems) and making industrial robots far more adaptable to constantly changing manufacturing and logistics environments.

_Source: nvidia | Published: 2026-09-10T16:30:35+00:00 | Score: 34.0 | ✨ AI-enriched_

5. [Physical AI Takes the Wheel: How the World’s Robotaxi Leaders Are Building With NVIDIA Technologies](https://blogs.nvidia.com/blog/robotaxi-leaders-full-stack-open-platform/)

The global robotaxi market — physical AI’s first commercial breakthrough — is projected to reach $400 billion by 2035, with over 6 million commercial vehicles in operation as driverless fleets are already moving people through some of the world’s busiest and most complex streets. Deploying a driverless vehicle is...

_Source: nvidia | Published: 2026-09-10T16:00:04+00:00 | Score: 34.0_

6. [d-Matrix Adopts NVIDIA NVLink Fusion for Rack-Scale XPU Deployment](https://blogs.nvidia.com/blog/d-matrix-nvlink-fusion/)

AI inference chipmaker d-Matrix today announced it will use NVLink Fusion to connect its next-generation Raptor XPUs to NVIDIA’s AI infrastructure platform — joining a growing roster of ecosystem partners. By connecting Raptor to NVIDIA NVLink scale-up and Spectrum-X scale-out networking, the NVIDIA MGX rack...

_Source: nvidia | Published: 2026-09-10T13:00:21+00:00 | Score: 34.0_

7. [GigaPath-Flash and GigaTIME-Flash: Toward population-scale discovery with efficient pathology foundation models](https://www.microsoft.com/en-us/research/blog/gigapath-flash-and-gigatime-flash-toward-population-scale-discovery-with-efficient-pathology-foundation-models/)

What if pathology foundation models could do more with less? GigaPath-Flash and GigaTIME-Flash cut computational demands while maintaining strong performance, opening the door to larger studies and broader exploration. The post GigaPath-Flash and GigaTIME-Flash: Toward population-scale discovery with efficient...

_Source: microsoft-research | Published: 2026-08-31T16:00:00+00:00 | Score: 30.0_

8. [Broadening access to Skala creates a faster path to predictive DFT](https://www.microsoft.com/en-us/research/blog/broadening-access-to-skala-creates-a-faster-path-to-predictive-dft/)

Skala 1.1, the updated deep-learning exchange-correlation functional from Microsoft Research, provides greater accuracy, expanded accessibility across the computational chemistry ecosystem, and a living benchmark to track computational performance. The post Broadening access to Skala creates a faster path to...

_Source: microsoft-research | Published: 2026-08-20T16:00:00+00:00 | Score: 30.0_

9. [MindTopo reveals VLMs’ spatial reasoning abilities](https://www.microsoft.com/en-us/research/blog/mindtopo-reveals-vlms-spatial-reasoning-abilities/)

A path, a fence, a knot. MindTopo sets a new benchmark for testing how AI understands topological relationships and highlights new opportunities to strengthen spatial reasoning and planning. The post MindTopo reveals VLMs’ spatial reasoning abilities appeared first on Microsoft Research .

_Source: microsoft-research | Published: 2026-08-12T16:00:00+00:00 | Score: 30.0_

10. [Rebuilding AUTOMATIC1111 with Gradio Workflow](https://huggingface.co/blog/gradio-workflow-1111)

No summary available.

_Source: huggingface | Published: 2026-09-10T00:00:00+00:00 | Score: 24.0_


## Key Trends This Batch
- ai-agents appeared in 4 high-priority items.
- openai appeared in 3 high-priority items.
- nvidia appeared in 3 high-priority items.

## Watchlist
- [viserys-agent](https://github.com/rizqinrr/viserys-agent)
- [recurrent-looped-tranformer](https://github.com/yifanzhang-pro/recurrent-looped-tranformer)
- [anything2explainer](https://github.com/Vincentwei1021/anything2explainer)
- [dream-loop](https://github.com/achimala/dream-loop)
- [Perplexity trusts GPT-6 Astra with end-to-end systems](https://openai.com/index/perplexity-improving-accuracy-with-astra)

---
Compiled from 29 normalized items and 14 selected highlights.
Generated at 2026-09-13T02:52:16.416246+00:00.
