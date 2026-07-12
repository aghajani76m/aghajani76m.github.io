---
layout: page
title: FARSIQA
description: An end-to-end, safety-aware Persian question-answering system built on FAIR-RAG for faithful reasoning over authoritative domain knowledge.
img: assets/img/projects/farsiqa/cover.png
importance: 2
category: research
---

<div class="text-center mb-4">
  <img
    src="{{ '/assets/img/projects/farsiqa/cover.png' | relative_url }}"
    alt="FARSIQA faithful Persian question-answering system"
    class="img-fluid rounded z-depth-1"
  >
</div>

<div class="d-flex flex-wrap gap-2 justify-content-center mb-4">
  <a
    class="btn btn-outline-primary"
    href="https://arxiv.org/abs/2510.25621"
    target="_blank"
    rel="noopener"
  >
    Paper
  </a>

<a
class="btn btn-outline-primary"
href="https://arxiv.org/pdf/2510.25621"
target="\_blank"
rel="noopener"

>

    PDF

  </a>
</div>

## Overview

**FARSIQA — Faithful & Advanced RAG System for Islamic Question Answering** is an end-to-end Persian question-answering system designed for a sensitive and knowledge-intensive domain where unsupported or misleading answers can have serious consequences.

The system applies the FAIR-RAG architecture to real-world Persian QA. It combines query validation, adaptive model selection, hybrid retrieval, evidence filtering, iterative gap analysis, and citation-grounded answer generation.

Unlike conventional single-pass RAG systems, FARSIQA does not immediately generate an answer from the first retrieved documents. It first determines whether the query is within scope, gathers evidence from multiple authoritative sources, evaluates evidence sufficiency, and performs targeted retrieval when information is still missing.

<div class="row row-cols-2 row-cols-md-4 g-3 text-center my-4">
  <div class="col">
    <div class="card h-100">
      <div class="card-body">
        <h3 class="mb-1">1.712M</h3>
        <small>Indexed text chunks</small>
      </div>
    </div>
  </div>

  <div class="col">
    <div class="card h-100">
      <div class="card-body">
        <h3 class="mb-1">735K</h3>
        <small>Source documents and Q&A records</small>
      </div>
    </div>
  </div>

  <div class="col">
    <div class="card h-100">
      <div class="card-body">
        <h3 class="mb-1">97%</h3>
        <small>Out-of-scope rejection accuracy</small>
      </div>
    </div>
  </div>

  <div class="col">
    <div class="card h-100">
      <div class="card-body">
        <h3 class="mb-1">74.3%</h3>
        <small>Answer correctness</small>
      </div>
    </div>
  </div>
</div>

## The Research Challenge

General-purpose language models can produce fluent responses even when they lack sufficient or authoritative evidence. This problem is especially important in specialized domains where questions may involve disputed interpretations, complex historical relations, or multiple pieces of supporting information.

Standard RAG pipelines also remain highly dependent on the first retrieval step. When the initial query fails to retrieve all required evidence, the generator may produce an incomplete or unsupported answer.

FARSIQA addresses these limitations by combining:

- explicit scope and safety validation,
- multi-hop query decomposition,
- domain-adapted semantic retrieval,
- hybrid dense and sparse search,
- iterative evidence-sufficiency assessment,
- and constrained, citation-grounded generation.

## Knowledge Base

The system operates over a large curated Persian knowledge base constructed from encyclopedic resources and expert-reviewed question-answering platforms.

<div class="text-center my-4">
  <img
    src="{{ '/assets/img/projects/farsiqa/knowledge-base.png' | relative_url }}"
    alt="FARSIQA Persian knowledge-base construction and indexing pipeline"
    class="img-fluid rounded z-depth-1"
  >
</div>

The corpus contains approximately:

- **431,000 encyclopedic documents**
- **304,000 question-answer records**
- **735,000 total source records**
- **1,712,000 indexed text chunks**

Encyclopedic articles were processed using recursive, semantically aware chunking. For Q&A sources, the original user question was attached to each corresponding answer chunk to preserve the relationship between the information need and the expert response.

Each chunk was indexed with source metadata to support evidence traceability and citation.

## Domain-adapted Retrieval

FARSIQA uses a combination of dense semantic retrieval and sparse keyword retrieval.

A Persian sentence-embedding model was fine-tuned on a custom dataset of **24,000 question–relevant passage–irrelevant passage triplets** from the target corpus. This domain adaptation produced a **16% improvement in Recall@3** over the original embedding model.

The final retrieval pipeline combines:

1. dense semantic retrieval,
2. BM25 keyword search,
3. Reciprocal Rank Fusion,
4. and LLM-based evidence filtering.

This combination improves semantic coverage while preserving exact matching for names, entities, and specialized terminology.

## System Architecture

<div class="text-center my-4">
  <img
    src="{{ '/assets/img/projects/farsiqa/architecture.png' | relative_url }}"
    alt="Architecture of the FARSIQA multi-stage agentic question-answering system"
    class="img-fluid rounded z-depth-1"
  >
  <p class="text-muted small mt-2">
    FARSIQA combines safety-aware query routing, hybrid retrieval, iterative evidence refinement, and faithful generation.
  </p>
</div>

The system is organized into four major phases.

### 1. Adaptive Query Processing

The input is first classified according to scope, safety, and complexity.

Queries may be categorized as:

- out of scope,
- unethical or unsafe,
- obvious,
- small,
- large,
- or reasoning-intensive.

Out-of-scope and inappropriate requests are rejected before retrieval. Valid requests are routed to an appropriate processing and generation strategy.

### 2. Hybrid Retrieval and Re-ranking

Complex questions are decomposed into focused sub-queries. For each sub-query, the system performs both semantic and keyword search over the Elasticsearch knowledge base.

Candidate documents are fused and re-ranked before being passed to the evidence-assessment layer.

### 3. Iterative Evidence Refinement

The FAIR-RAG refinement cycle filters irrelevant documents and applies Structured Evidence Assessment to determine which required findings are supported and which remain missing.

When evidence gaps remain, the system generates targeted new sub-queries and performs another retrieval cycle.

### 4. Faithful Answer Generation

The final generator receives only the filtered and validated evidence.

It is instructed to:

- ground claims exclusively in the retrieved sources,
- attach traceable citations,
- avoid unsupported external knowledge,
- present differing viewpoints neutrally when necessary,
- and acknowledge insufficient evidence rather than speculate.

## Safety and Responsible Answering

FARSIQA was designed as a research system for a sensitive domain, not as an authority issuing definitive religious judgments.

Its safeguards include:

- rejection of irrelevant and out-of-domain questions,
- refusal to generate unsupported answers,
- neutral presentation of conflicting views found in the evidence,
- explicit grounding in retrievable sources,
- and guidance to consult qualified authorities for requests involving religious rulings.

These mechanisms aim to reduce hallucination while preserving transparency about the limits of the system.

## Evaluation

The evaluation suite contained 800 questions across four categories:

- 500 multi-hop questions,
- 100 out-of-domain rejection questions,
- 100 noisy-context questions,
- and 100 simple or obvious questions.

The reported evaluation examined answer correctness, faithfulness, context relevance, robustness to noisy evidence, and the ability to reject questions outside the knowledge base.

<div class="text-center my-4">
  <img
    src="{{ '/assets/img/projects/farsiqa/robustness-results.png' | relative_url }}"
    alt="FARSIQA robustness, correctness, faithfulness, and negative-rejection results"
    class="img-fluid rounded z-depth-1"
  >
</div>

Key results include:

- **97.0% Negative Rejection Accuracy**
- **74.3% Answer Correctness**
- a substantial improvement over naive retrieval-generation baselines,
- and stronger performance on multi-hop and noisy-context questions.

The rejection result is especially important because a reliable domain-specific system must recognize when its knowledge base cannot support an answer.

## Iteration and Efficiency

The iterative refinement process consistently improved answer quality from one to three retrieval cycles.

<div class="text-center my-4">
  <img
    src="{{ '/assets/img/projects/farsiqa/iteration-tradeoff.png' | relative_url }}"
    alt="FARSIQA trade-off between iteration count, answer quality, token use, and latency"
    class="img-fluid rounded z-depth-1"
  >
</div>

Three iterations were selected as the optimal configuration:

- one iteration was faster but less reliable,
- two iterations provided a substantial improvement,
- three iterations produced the best overall quality–efficiency balance,
- and a fourth iteration increased cost and latency without meaningful quality gains.

## Dynamic Model Allocation

Different internal tasks require different levels of model capability.

FARSIQA dynamically allocates models for:

- query decomposition,
- evidence assessment,
- evidence filtering,
- query refinement,
- and final generation.

This strategy avoids using the largest model for every operation while preserving stronger reasoning capacity for the most demanding stages.

The reported dynamic configuration achieved the best rejection accuracy and was approximately **13% more cost-effective** than a static large-model configuration, with nearly identical token and API-call requirements.

## My Role

As the **first author and primary system engineer**, I contributed to:

- defining the research problem and system requirements,
- designing the complete FARSIQA architecture,
- constructing and preprocessing the Persian knowledge base,
- designing the hybrid Elasticsearch retrieval pipeline,
- creating the domain-specific retriever training dataset,
- fine-tuning and evaluating the embedding model,
- implementing adaptive routing and multi-agent components,
- integrating the FAIR-RAG iterative refinement process,
- designing the evaluation and ablation studies,
- and writing and preparing the research manuscript.

## Technology and Research Stack

`Python` · `LangChain` · `FastAPI` · `Elasticsearch` · `BM25` · `Dense Retrieval` · `Sentence Transformers` · `LLM Agents` · `FAIR-RAG` · `Prompt Engineering` · `Persian NLP` · `LLM-as-Judge`

## Limitations

The current research system has several known limitations:

- it processes queries independently and does not yet maintain conversational memory,
- its knowledge base does not cover the full diversity of Islamic scholarly traditions,
- its source distribution may reflect the perspectives most represented in the collected corpus,
- and iterative retrieval introduces additional latency compared with single-pass RAG.

These limitations are explicitly acknowledged because reliability requires transparency not only about system capabilities, but also about knowledge coverage and potential source bias.

## Research Significance

FARSIQA demonstrates how an advanced RAG architecture can be adapted to a low-resource language and a domain where faithfulness, refusal behavior, source traceability, and responsible generation are as important as answer fluency.

The project connects research in agentic RAG, Persian NLP, domain-adapted retrieval, trustworthy generation, and safety-aware question answering within a single evaluated end-to-end system.
