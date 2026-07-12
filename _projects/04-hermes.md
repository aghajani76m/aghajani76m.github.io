---
layout: page
title: HERMES
description: A human-guided, evidence-grounded multi-agent system supporting the complete scholarly workflow for long-form humanities research and writing.
img: assets/img/projects/hermes/cover.png
importance: 4
category: research
---

<div class="text-center mb-4">
  <img
    src="{{ '/assets/img/projects/hermes/cover.png' | relative_url }}"
    alt="HERMES evidence-grounded research and scholarly writing workflow"
    class="img-fluid rounded z-depth-1"
  >
</div>

<div class="d-flex flex-wrap justify-content-center gap-2 mb-4">
  <span class="badge rounded-pill text-bg-primary px-3 py-2">
    Ongoing Project
  </span>

  <span class="badge rounded-pill text-bg-light border px-3 py-2">
    Human-guided Research
  </span>

  <span class="badge rounded-pill text-bg-light border px-3 py-2">
    Persian Humanities
  </span>
</div>

## Overview

**HERMES — Humanities Evidence-grounded Research via Multi-agent Essay Synthesis** is an end-to-end research-assistance system designed to support long-form scholarly work in the humanities.

The system mirrors the complete academic workflow: defining and narrowing a research problem, locating and validating literature, extracting arguments and evidence, proposing an article structure, drafting sections iteratively, verifying citations, and producing documented LaTeX output.

HERMES is not designed to replace the scholar or independently determine the interpretation of a research topic. It is designed to reduce repetitive research work while preserving human judgment, source verification, interpretive control, and academic accountability.

<div class="row row-cols-1 row-cols-md-2 row-cols-lg-4 g-3 text-center my-4">
  <div class="col">
    <div class="card h-100">
      <div class="card-body">
        <h4 class="mb-2">End-to-End</h4>
        <small>From topic scoping to documented article output</small>
      </div>
    </div>
  </div>

  <div class="col">
    <div class="card h-100">
      <div class="card-body">
        <h4 class="mb-2">Human-guided</h4>
        <small>Mandatory scholar approval at critical decisions</small>
      </div>
    </div>
  </div>

  <div class="col">
    <div class="card h-100">
      <div class="card-body">
        <h4 class="mb-2">Evidence-grounded</h4>
        <small>Claims connected to real and verifiable sources</small>
      </div>
    </div>
  </div>

  <div class="col">
    <div class="card h-100">
      <div class="card-body">
        <h4 class="mb-2">Quality-gated</h4>
        <small>Independent review before advancing between stages</small>
      </div>
    </div>
  </div>
</div>

## The Problem

Existing AI writing tools often focus on isolated activities such as summarization, literature discovery, outline generation, or text completion.

This fragmented approach leaves the researcher responsible for manually transferring information between disconnected tools. More importantly, unconstrained generation can introduce unsupported claims, fabricated references, weak argument structure, and loss of scholarly control.

Long-form humanities research introduces additional challenges:

- sources may contain competing interpretations,
- arguments must be reconstructed rather than merely summarized,
- claims require traceable citations,
- article structure depends on the research question,
- and the scholar must retain control over interpretive decisions.

HERMES addresses these challenges through a staged, accountable workflow rather than a single-prompt generation process.

## Complete Research Workflow

<div class="text-center my-4">
  <img
    src="{{ '/assets/img/projects/hermes/complete-pipeline.png' | relative_url }}"
    alt="Complete HERMES scholarly research and writing pipeline"
    class="img-fluid rounded z-depth-1"
  >
  <p class="text-muted small mt-2">
    Each stage produces a reviewable artifact and advances only after quality review and scholar approval.
  </p>
</div>

The workflow contains the following major stages.

### 1. Topic Scoping

The system helps transform an initial idea into a focused and researchable topic.

The output may include:

- the central research question,
- scope boundaries,
- relevant concepts,
- proposed sub-questions,
- and potential methodological constraints.

The scholar reviews and approves the scoped topic before the project advances.

### 2. Literature Mining

The system searches for literature relevant to the approved research question and organizes candidate sources.

This stage focuses on:

- source discovery,
- bibliographic metadata,
- relevance assessment,
- removal of duplicate or weak sources,
- and preparation of a reviewable source collection.

The scholar determines which sources are accepted into the research corpus.

### 3. Argument and Evidence Extraction

Approved sources are processed to identify:

- primary claims,
- supporting evidence,
- key concepts,
- agreements and disagreements,
- methodological positions,
- and potentially useful quotations or passages.

The objective is not merely to summarize each source, but to create a structured evidence map that can support article-level reasoning.

### 4. Article Structuring

Using the approved topic and evidence map, the system proposes an article structure.

The proposed outline may contain:

- introduction and problem definition,
- theoretical or historical background,
- thematic sections,
- competing perspectives,
- analysis and synthesis,
- conclusion,
- and source allocation for each section.

The researcher may accept, revise, reorder, or reject the proposed structure.

### 5. Iterative Drafting

The article is generated section by section rather than in a single pass.

Each section is drafted using:

- the approved outline,
- section-specific evidence,
- writing requirements,
- previously approved sections,
- and citation constraints.

The researcher reviews each section before the workflow continues.

### 6. Citation and Consistency Review

Before final export, the system checks:

- whether claims are supported by the cited sources,
- whether citations correspond to the correct evidence,
- whether terminology is used consistently,
- whether sections follow the approved outline,
- and whether contradictions or unsupported statements remain.

### 7. Documented Output

The final deliverable is prepared as a structured scholarly document, including:

- approved article text,
- inline citations,
- bibliography,
- documented sources,
- section structure,
- and LaTeX-compatible output.

## Human-in-the-Loop Research

<div class="text-center my-4">
  <img
    src="{{ '/assets/img/projects/hermes/human-in-the-loop.png' | relative_url }}"
    alt="Human approval and revision checkpoints in HERMES"
    class="img-fluid rounded z-depth-1"
  >
</div>

Human approval is a structural requirement of HERMES, not an optional final review.

The primary checkpoints include:

- **Topic approval:** Is the research question meaningful and sufficiently focused?
- **Source approval:** Are the selected sources valid, relevant, and appropriate?
- **Outline approval:** Does the proposed structure reflect the intended interpretation?
- **Draft approval:** Does each generated section accurately represent the evidence and scholarly intent?

At each checkpoint, the researcher can:

- approve the proposed artifact,
- modify it directly,
- request targeted revision,
- remove unsuitable content,
- or return the project to an earlier stage.

This structure preserves scholarly agency and prevents automation from silently changing the research direction.

## Quality Gate

<div class="text-center my-4">
  <img
    src="{{ '/assets/img/projects/hermes/quality-gate.png' | relative_url }}"
    alt="HERMES quality-gate and revision decision process"
    class="img-fluid rounded z-depth-1"
  >
</div>

A dedicated critic component reviews the output of every major stage before it can proceed.

Depending on the stage, the quality gate evaluates criteria such as:

- compliance with the approved research scope,
- source relevance and credibility,
- evidence coverage,
- claim–source alignment,
- structural coherence,
- citation completeness,
- consistency with earlier approved decisions,
- and adherence to section-specific requirements.

The gate returns one of two high-level decisions:

```text
PASS → Send for scholar approval or advance
REVISE → Return actionable feedback to the current stage
```

This separation between generation and criticism reduces the risk that the same component both produces and unquestioningly approves its own output.

## Specialized Components

HERMES uses specialized components for distinct scholarly tasks rather than relying on one general-purpose prompt.

The system includes capabilities for:

- topic and problem formulation,
- literature retrieval,
- source screening,
- argument extraction,
- evidence mapping,
- outline proposal,
- section-level drafting,
- citation checking,
- quality criticism,
- and document generation.

Each component receives a constrained task, structured input, and an expected output format. This modular design makes the workflow easier to inspect, revise, and evaluate.

## Evidence-grounded Writing

Every generated section is expected to be grounded in the approved research corpus.

The system is designed to:

- avoid inventing references,
- distinguish source claims from generated synthesis,
- preserve source metadata,
- connect claims to supporting evidence,
- expose missing evidence,
- and acknowledge when the available sources cannot support a requested argument.

This approach is particularly important in humanities research, where a fluent paragraph may still misrepresent an author's position or combine incompatible interpretations.

## Example Output

<div class="text-center my-4">
  <img
    src="{{ '/assets/img/projects/hermes/output-example.png' | relative_url }}"
    alt="Example of a structured and citation-grounded HERMES article output"
    class="img-fluid rounded z-depth-1"
  >
</div>

A completed project can provide:

- the approved research brief,
- a curated bibliography,
- structured source notes,
- an evidence and argument map,
- the approved article outline,
- section-level drafts,
- claim–citation connections,
- and a documented LaTeX manuscript.

## My Role

As the **AI/NLP engineer and system designer**, I contributed to:

- defining the end-to-end scholarly workflow,
- translating research activities into modular system stages,
- designing the multi-component orchestration architecture,
- implementing literature-retrieval and RAG components,
- designing argument-extraction and evidence-grounding processes,
- creating human-approval checkpoints,
- designing the cross-stage quality-gate mechanism,
- implementing structured section-by-section drafting,
- designing citation-aware generation,
- and preparing documented LaTeX output.

## Technology Stack

`Python` · `LangChain` · `LLM Agents` · `Retrieval-Augmented Generation` · `Prompt Engineering` · `Vector Databases` · `Literature Retrieval` · `Faithful Generation` · `Human-in-the-loop Systems` · `LaTeX`

## Current Status

HERMES is an ongoing research and engineering project.

The current focus is on:

- improving source validation,
- strengthening claim-level traceability,
- formalizing quality criteria for each stage,
- evaluating long-form coherence,
- reducing citation errors,
- and designing systematic comparisons with existing research-assistance tools.

Quantitative evaluation results will be reported only after a controlled evaluation protocol and representative humanities research tasks have been completed.

## Design Principles

HERMES is guided by four central principles.

### Augmentation, Not Replacement

The system reduces repetitive work while leaving scholarly interpretation and final responsibility with the researcher.

### Evidence Before Generation

The workflow prioritizes source collection and evidence organization before long-form drafting.

### Reviewable Intermediate Artifacts

Every major stage produces an artifact that can be inspected, edited, accepted, or rejected.

### Accountability by Design

Human approvals, source traceability, quality gates, and documented outputs are integrated into the architecture rather than added after generation.

## Project Significance

HERMES explores how agentic AI can support scholarly research without collapsing the entire process into automated text generation.

Its central contribution is the design of a complete, human-governed research workflow in which AI assists with discovery, organization, synthesis, and drafting while preserving evidence traceability and researcher authority.
