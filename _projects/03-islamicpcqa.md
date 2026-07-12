---
layout: page
title: IslamicPCQA
description: A large-scale Persian dataset and benchmark for multi-hop complex question answering over unstructured Islamic text resources.
img: assets/img/projects/islamicpcqa/cover.png
importance: 3
category: research
---

<div class="text-center mb-4">
  <img
    src="{{ '/assets/img/projects/islamicpcqa/cover.png' | relative_url }}"
    alt="IslamicPCQA Persian multi-hop question-answering dataset"
    class="img-fluid rounded z-depth-1"
  >
</div>

<div class="d-flex flex-wrap gap-2 justify-content-center mb-4">
  <a
    class="btn btn-outline-primary"
    href="https://doi.org/10.1109/TASLPRO.2025.3587450"
    target="_blank"
    rel="noopener"
  >
    IEEE Paper
  </a>

<a
class="btn btn-outline-primary"
href="https://ieeexplore.ieee.org/document/11075543"
target="\_blank"
rel="noopener"

>

    IEEE Xplore

  </a>
</div>

## Overview

**IslamicPCQA** is a large-scale Persian dataset and benchmark for multi-hop complex question answering over unstructured textual resources.

The dataset was created to address a major limitation in Persian NLP: most existing Persian QA datasets focus on simple, single-paragraph questions, while many real-world information needs require combining evidence from multiple documents.

IslamicPCQA contains **12,282 manually constructed question-answer pairs** derived from nine Persian Islamic encyclopedias. Each question requires reasoning across at least two related paragraphs and is accompanied by annotated supporting facts that make the reasoning path explicit.

<div class="row row-cols-2 row-cols-md-4 g-3 text-center my-4">
  <div class="col">
    <div class="card h-100">
      <div class="card-body">
        <h3 class="mb-1">12,282</h3>
        <small>Question-answer pairs</small>
      </div>
    </div>
  </div>

  <div class="col">
    <div class="card h-100">
      <div class="card-body">
        <h3 class="mb-1">9</h3>
        <small>Persian encyclopedias</small>
      </div>
    </div>
  </div>

  <div class="col">
    <div class="card h-100">
      <div class="card-body">
        <h3 class="mb-1">637.7K</h3>
        <small>Valid graph edges</small>
      </div>
    </div>
  </div>

  <div class="col">
    <div class="card h-100">
      <div class="card-body">
        <h3 class="mb-1">80.44%</h3>
        <small>Best benchmark F1</small>
      </div>
    </div>
  </div>
</div>

## Research Motivation

Multi-hop questions cannot usually be answered by locating a single sentence or paragraph. They require a system to identify relationships between entities, retrieve evidence from multiple documents, and combine the retrieved facts through several reasoning steps.

This capability has been widely studied in English through datasets such as HotpotQA, but comparable resources for Persian remain limited.

IslamicPCQA was designed to support research on:

- Persian multi-hop reasoning,
- cross-document question answering,
- supporting-fact identification,
- machine reading comprehension,
- information retrieval over low-resource languages,
- and evaluation of multilingual language models.

## Dataset Construction

<div class="text-center my-4">
  <img
    src="{{ '/assets/img/projects/islamicpcqa/dataset-pipeline.png' | relative_url }}"
    alt="IslamicPCQA dataset-construction pipeline"
    class="img-fluid rounded z-depth-1"
  >
</div>

The construction process consisted of the following main stages:

1. collecting articles from nine Persian encyclopedias,
2. extracting and preprocessing the main textual content,
3. selecting informative paragraph representations,
4. constructing a directed hyperlink graph,
5. extracting related paragraph pairs,
6. designing multi-hop questions through human annotation,
7. annotating answers and supporting facts,
8. and conducting expert quality review.

The source resources included:

- WikiShia
- WikiFiqh
- WikiAhlolbait
- ImamatPedia
- IslamPedia
- WikiHaj
- WikiNoor
- WikiPasokh
- WikiHussain

## Hyperlink-Graph Infrastructure

The core dataset-construction mechanism is a directed graph derived from hyperlinks between encyclopedia pages.

<div class="text-center my-4">
  <img
    src="{{ '/assets/img/projects/islamicpcqa/hyperlink-graph.png' | relative_url }}"
    alt="Graph-based paragraph-pair selection for IslamicPCQA"
    class="img-fluid rounded z-depth-1"
  >
</div>

Each graph node represents a processed paragraph associated with an encyclopedia page. A directed edge connects two nodes when a hyperlink in the source paragraph refers to the destination page.

Several paragraph-selection strategies were evaluated. The selected approach used the first informative sentences of each page because they generally provide:

- consistent paragraph length,
- broad contextual information,
- clear entity references,
- and sufficient content for constructing complex questions.

The initial graph contained approximately:

- **155,700 nodes**
- **1.4 million hyperlink edges**

After removing duplicate links, invalid pages, empty content, and unsuitable paragraph pairs, the final graph contained:

- **115,000 valid nodes**
- **637,700 valid edges**

The graph provided a scalable mechanism for recommending related paragraph pairs to annotators.

## Human Annotation and Quality Assurance

<div class="text-center my-4">
  <img
    src="{{ '/assets/img/projects/islamicpcqa/annotation-workflow.png' | relative_url }}"
    alt="Human annotation and quality-control workflow for IslamicPCQA"
    class="img-fluid rounded z-depth-1"
  >
</div>

A dedicated annotation platform presented candidate paragraph pairs sampled from the graph.

More than **25 graduate annotators** in computer engineering and artificial intelligence from **five Iranian universities** participated in the data-creation process.

Annotators were trained using instructional documents, videos, and direct guidance. Producing each valid question required approximately three to five minutes, resulting in more than **800 hours of annotation work**.

Each final record contains:

- two related source paragraphs,
- a multi-hop question,
- the correct answer,
- sentence-level supporting facts,
- the question type,
- the answer type,
- and metadata describing the reasoning structure.

Generated samples were continuously monitored and subsequently reviewed by an expert quality-control team before final acceptance.

## Multi-hop Reasoning

IslamicPCQA includes five broad reasoning patterns.

These patterns include:

- bridge reasoning through an intermediate entity,
- comparison between entities or properties,
- multi-feature constraint reasoning,
- intermediary-entity attribute reasoning,
- and combinations of cross-paragraph evidence.

The most frequent category requires identifying an intermediary entity in one paragraph and using it to retrieve the final answer from another paragraph.

This variety helps prevent the dataset from representing multi-hop reasoning as a single fixed template.

## Supporting Facts

A distinguishing characteristic of IslamicPCQA is its sentence-level supporting-fact annotation.

For each source paragraph, annotators specify the exact sentences required to construct the reasoning path and locate the answer.

This enables researchers to evaluate not only whether a model predicts the correct answer, but also whether it identifies the correct evidence.

Supporting-fact annotation is useful for:

- interpretable question answering,
- explainable retrieval,
- evidence selection,
- multi-step reasoning evaluation,
- and training systems that expose their reasoning sources.

## Dataset Splits

The final dataset is divided into:

| Split       |    Samples |
| ----------- | ---------: |
| Training    |      9,000 |
| Development |      1,641 |
| Test        |      1,641 |
| **Total**   | **12,282** |

## Evaluation Settings

Two benchmark settings were introduced.

### Distractor Setting

Each question is provided with:

- two golden evidence paragraphs,
- and eight topically similar distractor paragraphs.

The model must identify the relevant context and extract the correct answer while ignoring misleading evidence.

### Fullwiki Setting

The system must retrieve relevant paragraphs from the complete document collection before predicting the answer.

This setting evaluates both retrieval and reading comprehension and is substantially more difficult than the controlled distractor condition.

## Benchmark Results

Several multilingual and Persian language models were fine-tuned and evaluated using Exact Match and token-level F1.

<div class="text-center my-4">
  <img
    src="{{ '/assets/img/projects/islamicpcqa/benchmark-results.png' | relative_url }}"
    alt="IslamicPCQA benchmark results for Persian and multilingual language models"
    class="img-fluid rounded z-depth-1"
  >
</div>

The strongest reported model was **XLM-RoBERTa**, achieving in the Distractor Setting:

- **80.44% F1**
- **67.33% Exact Match**

In the more demanding Fullwiki Setting, XLM-RoBERTa achieved:

- **72.86% F1**

The results show that multilingual pretraining, Persian-language resources, and effective retrieval substantially improve performance on Persian multi-hop QA.

## My Role

As a **co-author and core contributor**, I contributed to:

- designing the graph-based dataset-construction framework,
- collecting and preprocessing Persian encyclopedia content,
- developing the hyperlink-based paragraph-pair generation pipeline,
- designing the annotation workflow,
- coordinating dataset creation and quality control,
- defining complex multi-hop reasoning structures,
- preparing model-training and benchmark experiments,
- fine-tuning Persian and multilingual language models,
- analyzing experimental results,
- and preparing the research manuscript.

## Technology and Research Stack

`Python` · `Persian NLP` · `Graph Theory` · `Web Crawling` · `Human-in-the-loop Annotation` · `XLM-RoBERTa` · `ParsBERT` · `mBERT` · `mT5` · `PyTorch` · `Transformers` · `Information Retrieval` · `Multi-hop QA`

## Limitations

IslamicPCQA has several known limitations:

- its sources are restricted to Persian Islamic encyclopedias,
- topic and perspective distributions reflect the selected source collection,
- consistency can be further improved through additional multi-review annotation,
- and generalization to unrelated domains or languages requires further validation.

These limitations also identify useful directions for future work, including broader source diversity, more complex reasoning chains, and expansion to additional Persian domains.

## Research Significance

IslamicPCQA provides a reusable methodology for constructing multi-hop datasets from unstructured resources in low-resource languages.

Its contribution extends beyond one specialized domain: the same hyperlink-graph and human-annotation framework can be adapted to Persian scientific, historical, legal, medical, and educational corpora where questions require evidence from multiple documents.
