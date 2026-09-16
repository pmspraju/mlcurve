---
title: "MLCurve Digest - 2026-09-16"
date: 2026-09-16 03:05:26 +0000
layout: post
source: mlcurve-digest
---

## TL;DR
- ai-sucks-butt is gaining traction (863 stars, score 31.26).
- recurrent-looped-tranformer is gaining traction (834 stars, score 20.68).
- ai-data-extractor is gaining traction (823 stars, score 20.46).
- reelbench-skills is gaining traction (697 stars, score 17.94).
- nvidia published ‘Now We Can Know Everything and Do Anything,’ Jensen Huang Says at Dreamforce (score 44.0).

## Top Open Source Repos
1. [ai-sucks-butt](https://github.com/ai-sucks-butt/ai-sucks-butt)

The project hosts a static site that aggregates studies, articles, and community‑submitted examples highlighting the shortcomings, risks, and failures of current AI tools, with a discussion thread for contributors to add new evidence. For AI/ML practitioners, having a centralized, openly curated collection of concrete critiques helps surface real‑world limitations—such as hallucinations, security vulnerabilities, and productivity losses—so they can more accurately assess trade‑offs and design safer, more reliable systems.

_Source: ai | Published: 2026-09-14T04:02:58+00:00 | Score: 31.26 | Stars: 863 | ✨ AI-enriched_

2. [recurrent-looped-tranformer](https://github.com/yifanzhang-pro/recurrent-looped-tranformer)

The Recurrent Looped Transformer (RLT) pairs a causal encoder with a recurrent decoder that preserves the decoder’s final hidden state and layer‑wise sliding‑window attention cache across every prompt and response token, yielding a latent computation path whose structural depth grows with sequence length while keeping per‑token work fixed. It matters now because persistent state and unbounded temporal depth directly address the growing demand for models that can maintain coherent reasoning over very long contexts and enable consistent reinforcement‑learning replay, while its hardware‑aware design promises more efficient training and inference for emerging LLM applications.

_Source: llm | Published: 2026-09-12T19:02:46+00:00 | Score: 20.68 | Stars: 834 | ✨ AI-enriched_

3. [ai-data-extractor](https://github.com/kruzovic7/ai-data-extractor)

The ai-data-extractor project offers a free, open‑source tool that pulls chat logs from a range of AI coding assistants—including Claude Code, Cursor, Windsurf, Aider, and Cline/Roo Code—into a structured, exportable format. For AI/ML practitioners, ready access to these interaction histories enables systematic analysis, debugging, and fine‑tuning of prompt engineering workflows, which is increasingly valuable as code‑generation assistants become integral to development pipelines.

_Source: ai | Published: 2026-09-11T18:12:58+00:00 | Score: 20.46 | Stars: 823 | ✨ AI-enriched_

4. [reelbench-skills](https://github.com/eternityspring/reelbench-skills)

Reelbench‑skills supplies a command‑line skill that automatically splits an AI‑generated video into shot‑level segments, measures cut points and motion with ffmpeg, and uses a language model to label shot type, camera movement, and description while enforcing 14 quality‑gate checks and outputting an interactive HTML report. It matters now because the rapid growth of AI video generation creates a need for fast, reproducible, and quantitative quality assessment—something manual “拉片” cannot scale, and Reelbench‑skills offers a zero‑dependency, code‑first solution for practitioners to validate and improve their video pipelines.

_Source: ai | Published: 2026-09-11T04:55:49+00:00 | Score: 17.94 | Stars: 697 | ✨ AI-enriched_


## Research and Company Updates
1. [‘Now We Can Know Everything and Do Anything,’ Jensen Huang Says at Dreamforce](https://blogs.nvidia.com/blog/jensen-huang-dreamforce/)

Salesforce and NVIDIA unveiled Koa, the company’s first CRM reasoning model built on NVIDIA’s Nemotron 3 Super architecture, during the Dreamforce keynote where Jensen Huang highlighted the “know everything, do anything” vision. The model lets enterprise AI agents reliably handle complex, multistep sales, marketing and support tasks while keeping data inside the customer’s trusted environment, delivering more accurate automation and lower token‑costs than generic frontier models.

_Source: nvidia | Published: 2026-09-15T22:24:34+00:00 | Score: 44.0 | ✨ AI-enriched_

2. [From Megawatts to Tokens: How NVIDIA Maximizes AI Factory Production](https://blogs.nvidia.com/blog/from-megawatts-to-tokens-how-nvidia-maximizes-ai-factory-production/)

NVIDIA published a blog post titled “From Megawatts to Tokens: How NVIDIA Maximizes AI Factory Production,” unveiling its DSX platform—particularly the DSX MaxLPS dynamic‑power‑allocation software and Emerald AI Conductor—that lets AI factories receive grid signals, reclaim stranded capacity, and increase token throughput within a fixed megawatt budget. This matters because power is the dominant cost driver for AI factories; boosting tokens per watt translates directly into higher revenue, lower token cost, and the ability to scale AI workloads without expanding the power grid.

_Source: nvidia | Published: 2026-09-15T16:55:59+00:00 | Score: 44.0 | ✨ AI-enriched_

3. [AI Infra Summit: NVIDIA Vera Rubin and DSX Platform Advancements Showcase Energy Efficiencies of Optimizing Tokens Per Watt for AI Factories](https://blogs.nvidia.com/blog/ai-infra-summit-vera-rubin-dsx-energy-efficiencies-tokens-per-watt-ai-factories/)

NVIDIA announced its Vera Rubin AI‑factory platform paired with the DSX MaxLPS power‑optimization suite, showing up to 1.4× more tokens per megawatt and a 24% increase in cluster token throughput (19 nodes delivering the same power as 16 full‑power nodes) on Lambda’s Blackwell servers. These efficiency gains let AI factories pack up to 40% more GPU capacity into a fixed power envelope, dramatically lowering energy costs and making large‑scale, agentic AI workloads economically viable.

_Source: nvidia | Published: 2026-09-15T16:55:40+00:00 | Score: 44.0 | ✨ AI-enriched_

4. [Your Agent Aced the Task. Will It Do It Again?](https://huggingface.co/blog/ibm-research/altk-evolve-consistency)

Hugging Face published a September 15 2026 blog post announcing the release of “consistency guidelines” and a “Consistency Analyzer” built into the ALTK‑Evolve framework, which diagnose flip‑prone decision points in an agent’s trajectory and automatically inject reusable guidelines to halve the consistency gap between average success (Mean@k) and guaranteed success (Pass^k). This matters because it tackles a core reliability issue—agents that can solve a task once but may fail on repeat attempts—making AI agents far more dependable for mission‑critical workloads such as financial reconciliation or contract verification.

_Source: huggingface | Published: 2026-09-15T16:00:44+00:00 | Score: 44.0 | ✨ AI-enriched_

5. [How Fyxer built an AI executive assistant people trust](https://openai.com/index/fyxer)

Fyxer uses OpenAI models, fine-tuning, memory, and real user feedback to organize inboxes and draft emails in each user’s voice.

_Source: openai | Published: 2026-09-14T12:00:00+00:00 | Score: 40.0_

6. [Perplexity trusts GPT-6 Astra with end-to-end systems](https://openai.com/index/perplexity-improving-accuracy-with-astra)

Perplexity uses Astra to write communications, change software, and monitor production systems, and checks in much less frequently than with earlier models.

_Source: openai | Published: 2026-09-14T00:00:00+00:00 | Score: 40.0_

7. [Cognition helps Devin test its own work with GPT‑6 Astra](https://openai.com/index/cognition-devin-testing-with-astra)

GPT‑6 Astra improves Devin’s ability to test software and show that it works, with the goal of helping engineers review less code and ship more.

_Source: openai | Published: 2026-09-11T16:00:00+00:00 | Score: 30.0_

8. [GigaPath-Flash and GigaTIME-Flash: Toward population-scale discovery with efficient pathology foundation models](https://www.microsoft.com/en-us/research/blog/gigapath-flash-and-gigatime-flash-toward-population-scale-discovery-with-efficient-pathology-foundation-models/)

What if pathology foundation models could do more with less? GigaPath-Flash and GigaTIME-Flash cut computational demands while maintaining strong performance, opening the door to larger studies and broader exploration. The post GigaPath-Flash and GigaTIME-Flash: Toward population-scale discovery with efficient...

_Source: microsoft-research | Published: 2026-08-31T16:00:00+00:00 | Score: 30.0_

9. [Broadening access to Skala creates a faster path to predictive DFT](https://www.microsoft.com/en-us/research/blog/broadening-access-to-skala-creates-a-faster-path-to-predictive-dft/)

Skala 1.1, the updated deep-learning exchange-correlation functional from Microsoft Research, provides greater accuracy, expanded accessibility across the computational chemistry ecosystem, and a living benchmark to track computational performance. The post Broadening access to Skala creates a faster path to...

_Source: microsoft-research | Published: 2026-08-20T16:00:00+00:00 | Score: 30.0_

10. [MindTopo reveals VLMs’ spatial reasoning abilities](https://www.microsoft.com/en-us/research/blog/mindtopo-reveals-vlms-spatial-reasoning-abilities/)

A path, a fence, a knot. MindTopo sets a new benchmark for testing how AI understands topological relationships and highlights new opportunities to strengthen spatial reasoning and planning. The post MindTopo reveals VLMs’ spatial reasoning abilities appeared first on Microsoft Research .

_Source: microsoft-research | Published: 2026-08-12T16:00:00+00:00 | Score: 30.0_


## Key Trends This Batch
- nvidia appeared in 3 high-priority items.
- openai appeared in 3 high-priority items.
- microsoft-research appeared in 3 high-priority items.

## Watchlist
- [ai-sucks-butt](https://github.com/ai-sucks-butt/ai-sucks-butt)
- [recurrent-looped-tranformer](https://github.com/yifanzhang-pro/recurrent-looped-tranformer)
- [ai-data-extractor](https://github.com/kruzovic7/ai-data-extractor)
- [reelbench-skills](https://github.com/eternityspring/reelbench-skills)
- [‘Now We Can Know Everything and Do Anything,’ Jensen Huang Says at Dreamforce](https://blogs.nvidia.com/blog/jensen-huang-dreamforce/)

---
Compiled from 28 normalized items and 14 selected highlights.
Generated at 2026-09-16T03:05:26.223645+00:00.
