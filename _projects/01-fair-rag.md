---
layout: page
title: FAIR-RAG
description: An evidence-driven agentic RAG framework that identifies missing information and iteratively refines retrieval for complex multi-hop questions.
img: assets/img/projects/fair-rag/cover.png
importance: 1
category: research
---

<div class="text-center mb-4">
  <img
    src="{{ '/assets/img/projects/fair-rag/cover.png' | relative_url }}"
    alt="FAIR-RAG project cover"
    class="img-fluid rounded z-depth-1"
  >
</div>

<div class="d-flex flex-wrap gap-2 justify-content-center mb-4">
  <a
    class="btn btn-outline-primary"
    href="https://arxiv.org/abs/2510.22344"
    target="_blank"
    rel="noopener"
  >
    Paper
  </a>

<a
class="btn btn-outline-primary"
href="https://arxiv.org/pdf/2510.22344"
target="\_blank"
rel="noopener"

>

    PDF

  </a>
</div>

## Overview

**FAIR-RAG — Faithful Adaptive Iterative Refinement for Retrieval-Augmented Generation** is an agentic RAG framework designed for complex, multi-hop questions that cannot be reliably answered through a single retrieval step.

Instead of assuming that the initially retrieved context is sufficient, FAIR-RAG explicitly evaluates the available evidence, identifies unresolved information needs, and generates targeted follow-up queries. This process continues until the evidence is sufficiently comprehensive for a grounded final answer.

<div class="row row-cols-2 row-cols-md-4 g-3 text-center my-4">
  <div class="col">
    <div class="card h-100">
      <div class="card-body">
        <h3 class="mb-1">0.453</h3>
        <small>HotpotQA F1</small>
      </div>
    </div>
  </div>

  <div class="col">
    <div class="card h-100">
      <div class="card-body">
        <h3 class="mb-1">+8.3</h3>
        <small>F1 points over the strongest iterative baseline</small>
      </div>
    </div>
  </div>

  <div class="col">
    <div class="card h-100">
      <div class="card-body">
        <h3 class="mb-1">4</h3>
        <small>QA benchmarks</small>
      </div>
    </div>
  </div>

  <div class="col">
    <div class="card h-100">
      <div class="card-body">
        <h3 class="mb-1">2–3</h3>
        <small>Effective refinement iterations</small>
      </div>
    </div>
  </div>
</div>

## Research Problem

Standard RAG systems usually retrieve a fixed set of documents and immediately generate an answer. This approach is fragile for questions that require multiple pieces of evidence, entity resolution, comparison, or several dependent reasoning steps.

A weak initial query may retrieve only part of the required information. Existing iterative systems can also propagate noise when they use an entire generated answer as the next retrieval query.

FAIR-RAG addresses this problem by making **evidence sufficiency**, rather than generation alone, the central control signal of the pipeline.

## Core Contributions

### Structured Evidence Assessment

The central module, **Structured Evidence Assessment (SEA)**, converts the original question into a checklist of required findings. It then audits the accumulated evidence against that checklist and distinguishes between:

- confirmed findings,
- unsupported requirements,
- and explicit information gaps.

These gaps become actionable signals for the next retrieval cycle.

### Gap-driven Query Refinement

Rather than rewriting the original query generically, FAIR-RAG creates focused sub-queries that target only the missing information. Confirmed findings can be reused to make subsequent searches more precise.

### Evidence-grounded Generation

The final answer is generated only after the evidence-assessment stage determines that the context is sufficiently complete. The generator is constrained to use the validated evidence and provide traceable citations.

### Adaptive Resource Allocation

The framework can assign different language models to different tasks according to their complexity, balancing answer quality, computational cost, and latency.

## System Architecture

<div class="text-center my-4">
  <img
    src="{{ '/assets/img/projects/fair-rag/architecture.png' | relative_url }}"
    alt="FAIR-RAG architecture and iterative evidence-refinement pipeline"
    class="img-fluid rounded z-depth-1"
  >
  <p class="text-muted small mt-2">
    FAIR-RAG progressively retrieves, filters, evaluates, and refines evidence before final generation.
  </p>
</div>

The workflow contains four main stages:

1. **Initial query analysis and adaptive routing**
2. **Query decomposition and retrieval**
3. **Iterative filtering, evidence assessment, and query refinement**
4. **Faithful answer generation from validated evidence**

## Structured Evidence Assessment

<div class="text-center my-4">
  <img
    src="{{ '/assets/img/projects/fair-rag/sea-module.png' | relative_url }}"
    alt="Structured Evidence Assessment and information-gap analysis"
    class="img-fluid rounded z-depth-1"
  >
</div>

SEA differs from a conventional relevance classifier. It does not merely ask whether a document is related to the question. It asks whether the **entire evidence set supports every informational requirement needed to answer the question**.

This provides an interpretable stopping criterion and prevents the pipeline from terminating simply because it has retrieved several topically related documents.

## Experimental Results

FAIR-RAG was evaluated under a unified experimental setup on:

- HotpotQA
- 2WikiMultiHopQA
- MusiQue
- TriviaQA

The adaptive three-iteration configuration achieved:

- **0.453 F1 on HotpotQA**
- **0.320 F1 on 2WikiMultiHopQA**
- **0.264 F1 on MusiQue**
- **0.731 F1 on TriviaQA**

Under the controlled comparison reported in the paper, FAIR-RAG outperformed representative standard, conditional, reasoning-based, and iterative RAG baselines, with the largest gains appearing on complex multi-hop tasks.

<div class="text-center my-4">
  <img
    src="{{ '/assets/img/projects/fair-rag/benchmark-results.png' | relative_url }}"
    alt="FAIR-RAG benchmark results compared with representative RAG baselines"
    class="img-fluid rounded z-depth-1"
  >
</div>

## Iteration–Efficiency Trade-off

The ablation study showed that iterative evidence gathering is valuable for complex questions, but unlimited iteration is not optimal.

For multi-hop datasets, the strongest balance between answer quality and resource consumption was generally reached after two or three iterations. Additional cycles increased API calls and token consumption while offering limited or negative quality gains.

<div class="text-center my-4">
  <img
    src="{{ '/assets/img/projects/fair-rag/iteration-ablation.png' | relative_url }}"
    alt="Trade-off between refinement iterations, answer quality, and computational cost"
    class="img-fluid rounded z-depth-1"
  >
</div>

## My Role

As the **first author and primary framework designer**, I contributed to:

- defining the FAIR-RAG research problem and architecture,
- designing the Structured Evidence Assessment methodology,
- developing the gap-driven adaptive query-refinement strategy,
- implementing and integrating the multi-stage pipeline,
- designing the controlled benchmark evaluation,
- conducting ablation and component-level analyses,
- and writing and preparing the research manuscript.

## Technology and Research Stack

`Python` · `LLM Agents` · `Retrieval-Augmented Generation` · `FlashRAG` · `Faiss` · `Dense Retrieval` · `Prompt Engineering` · `Llama 3` · `Multi-hop QA` · `LLM-as-Judge Evaluation`

## Research Significance

FAIR-RAG demonstrates that reliable retrieval-augmented reasoning requires more than repeatedly retrieving documents. The system must explicitly represent what has been established, what remains unknown, and what evidence is still needed.

This evidence-driven perspective is directly relevant to trustworthy AI, automated fact-checking, scientific question answering, and other knowledge-intensive applications where unsupported or incomplete answers can have significant consequences.
