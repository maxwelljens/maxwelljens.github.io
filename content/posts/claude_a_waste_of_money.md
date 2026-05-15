---
title: "Claude: A Waste of Money"
description: "DeepSeek V4 has made Claude and other premium AI subscriptions almost impossible to justify on a cost-benefit basis."
tags: ["technology", "AI"]
cover:
  image: /claude_waste_of_money/card.jpg
date: 2026-05-15
---

DeepSeek V4 is here. Not a press release, not a carefully curated blog post
with cherry-picked benchmarks, but [a 58-page research
paper](https://arxiv.org/pdf/2601.07372) with nothing held back. And the
conclusion it forces is uncomfortable for anyone paying twenty dollars a month
for a premium AI subscription: **Claude is a waste of money.**

This is not hyperbole. The numbers are public, and they are absurd. Depending
on whether there is a discount or not, DeepSeek-V4 can be **30 times cheaper
than Anthropic's Claude**. Even without a discount, you are looking at 8 to 20
times less. That is not a small difference. That is the kind of difference that
makes you stop and ask what exactly you are paying for.

{{< callout type="note" >}}
Two Minute Papers has a nice breakdown in video format
[here](https://www.youtube.com/watch?v=p7K3xfViWCE).
{{< /callout >}}

## The Benchmarks

If you were paying 30 times more for a clearly superior product, you could make
a case for it, but you are not. Look at the numbers:

DeepSeek-V4-Pro on the maximum reasoning effort mode scores 90.2% on HLE, which
is one of the hardest "trust me bro" benchmarks in existence. Claude Opus
4.6-Max? 89.1%. On Apex, DeepSeek hits 85.9% against Claude's 78.1%. On
Codeforces rating, DeepSeek scores 3206, matching GPT-5.4 and leaving Claude in
the dust. On long-context retrieval, DeepSeek's MMR score of 92.9 crushes
Claude's 76.3. On CorpusQA accuracy at one million tokens, it is 71.7 against
53.8.

![DeepSeek-V4-Pro benchmarks graph](/claude_waste_of_money/trust_me_bro.png)

For the vast majority of real-world tasks, there is no meaningful gap. In
several important categories, DeepSeek outright wins. Yet you pay a fraction of
the cost, or nothing at all if you somehow manage to self-host all 1 trillion
parameters. This is the first time an open model has matched or beaten closed
frontier models at this breadth of tasks, and it happened faster than almost
anyone predicted.

## A Million Tokens for Free

A million-token context window used to be a flagship feature that justified
enterprise pricing. Google made a whole product launch out of it with Gemini. I
remember flipping out about it two years ago. Now DeepSeek hands it to you for
free in open weights. Ask it to inhale 1,500 pages of dense documentation, and
it will.

The engineering is worth understanding because it explains how this is even
possible. The transformer's vanilla attention mechanism has quadratic
complexity: double the context length, quadruple the compute. This is the
bottleneck that makes long contexts ruinously expensive for most models.
DeepSeek broke through it with a hybrid attention architecture combining
Compressed Sparse Attention and Heavily Compressed Attention.

Think of it like reading a book. You cannot process every word simultaneously,
so you summarise. DeepSeek does this at three levels:

1. **Token-level compression**: summarise each paragraph into a sentence. Keep
the book. Search it faster.

2. **Heavily compressed attention**: look at the table of contents. If each
chapter has a short name, you grasp the whole story at a glance. A 128-to-1
compression.

3. **Compressed sparse attention**: use an index. Searching for fights in a
novel? The index gives you the top five pages. The model attends only to what
matters.

Three layers: summaries, structure, index. Together they reduce KV-cache memory
needs by approximately 90%. Squashing 100 words into a storage space of 10
without losing every piece of information. The benchmarks back it up: on MRCR,
retrieval remains remarkably stable within 128K tokens and stays strong all the
way to one million.

## The Efficiency Leap

The previous DeepSeek-V3.2 was already efficient. DeepSeek-V4 is not an
improvement on it. It is a different category of efficiency entirely. In a
one-million-token context, DeepSeek-V4-Pro requires only **27% of the
single-token FLOPs** and **10% of the KV-cache** compared with V3.2. The Flash
model is more extreme still: 10% of the FLOPs and 7% of the KV-cache.

![DeepSeek-V4-Pro TFLOP requirements](/claude_waste_of_money/efficiency.png)

To translate: the Pro model needs about three times less computing power than
the previous generation for the same output. Flash needs about ten times less.
This is not incremental. This is a generational leap that reshapes the cost
calculus of running large-scale AI inference. Any company relying on Claude or
GPT for heavy inference workloads could achieve comparable results, results
that match or beat the frontier, at a fraction of the operational cost, or by
self-hosting entirely.

Two architectural innovations deserve specific mention because they are the
kind of thing that makes you stop and reread the paper. Manifold-Constrained
Hyper-Connections replace standard residual connections with something more
mathematically principled: the residual mapping matrix is constrained to the
manifold of doubly stochastic matrices, ensuring the spectral norm stays
bounded by one. In plain terms, it stops signal from exploding or vanishing
across deep stacks of layers. Muon, the new optimiser, replaces AdamW for most
modules and converges faster with better stability. DeepSeek is not just
scaling up, but are rethinking fundamentals.

## What DeepSeek Lacks

It would be dishonest to pretend DeepSeek V4 has no weaknesses. It has two
notable ones.

For one, it is unimodal: no images, no audio. It is blind and deaf, at least
for now. If your workflow involves heavy image analysis or multimodal
reasoning, Claude still has an edge, though it is hard to imagine that edge
surviving the next twelve months. If you need that edge, maybe combine with
Qwen.

The paper also admits something that is rare and genuinely refreshing: two
techniques used to stabilise training, Anticipatory Routing and SwiGLU
Clamping, work effectively, but the creators are not entirely sure why. This
is not the polished corporate non-answer you get from most AI companies. This
is a real research paper with real admissions of uncertainty. The transparency
is admirable, but it does mean there are open questions about behaviour under
certain edge cases.

Context window performance also degrades as you approach the limits. Models
forget, drift, hallucinate. More text means less truth. This is not a DeepSeek
problem, it is a universal one, but nevertheless worth knowing.

## The Trajectory

The gap between open and closed models is not closing. It has closed. On
knowledge benchmarks, DeepSeek-V4-Pro sets a new state-of-the-art for open
models, surpassing all prior open-source baselines by a margin of 20 absolute
percentage points on SimpleQA. On reasoning, it matches or beats the frontier.
On code, it is competitive with GPT-5.4, which is the first open model to
achieve this. On agents, it approaches Claude Opus 4.5. On long-context, it
surpasses Gemini-3.1-Pro.

None of this was supposed to happen this fast. The conventional wisdom a year
ago was that open models would trail the frontier by 12 to 18 months
indefinitely. DeepSeek-V4 trails by perhaps 3 to 6 months in a few narrow
categories and has pulled ahead in others. The proprietary incumbents are
running out of road.

## Conclusion

We are witnessing something unprecedented: frontier-level intelligence at a
price that is approaching zero. A 1.6 trillion parameter model. A million
tokens of context. Benchmark scores that match or beat the best proprietary
systems. Open weights. Free to use, cheap to run, available to self-host. The
phrase "too cheap to meter" used to be an aspiration. It is becoming a
description.

If you are still paying for Claude without having tried DeepSeek-V4, you are
not paying for quality. You are paying for inertia, for brand recognition, for
American datacentres, and for the comfort of a familiar chat window. Those are
not nothing, but they are not worth 30 times the price.
