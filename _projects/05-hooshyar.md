---
layout: page
title: HOOSHYAR
description: An explainable AI advisory system that evaluates fraud-risk indicators in online classified listings and helps users make safer transaction decisions.
img: assets/img/projects/hooshyar/cover.png
importance: 1
category: applied-ai
---

<div class="text-center mb-4">
  <img
    src="{{ '/assets/img/projects/hooshyar/cover.png' | relative_url }}"
    alt="HOOSHYAR explainable fraud-risk advisory for online classified listings"
    class="img-fluid rounded z-depth-1"
  >
</div>

<div class="d-flex flex-wrap justify-content-center gap-2 mb-4">
  <span class="badge rounded-pill text-bg-primary px-3 py-2">
    Ongoing Project
  </span>

  <span class="badge rounded-pill text-bg-light border px-3 py-2">
    Applied AI
  </span>

  <span class="badge rounded-pill text-bg-light border px-3 py-2">
    Trust & Safety
  </span>

  <span class="badge rounded-pill text-bg-light border px-3 py-2">
    Explainable Risk Advisory
  </span>
</div>

## Overview

**HOOSHYAR** is an explainable AI advisory system designed to help users assess risk indicators in online classified listings before contacting a seller, transferring money, or proceeding with a transaction.

The system examines multiple signals—including listing text, images, price, structured attributes, location information, communication options, and internal consistency—and converts them into a transparent risk profile.

Rather than declaring that a listing or seller is fraudulent, HOOSHYAR provides:

- a probabilistic risk assessment,
- positive and reassuring indicators,
- explainable warning signals,
- uncertainty information,
- and practical transaction-safety recommendations.

The project is designed for integration with a large online-classifieds platform through a viewer-side add-on, while also supporting a standalone web-based MVP.

<div class="row row-cols-1 row-cols-md-2 row-cols-lg-4 g-3 text-center my-4">
  <div class="col">
    <div class="card h-100">
      <div class="card-body">
        <h4 class="mb-2">Multi-signal</h4>
        <small>Text, image, price, metadata, and behavioral indicators</small>
      </div>
    </div>
  </div>

  <div class="col">
    <div class="card h-100">
      <div class="card-body">
        <h4 class="mb-2">Explainable</h4>
        <small>Every warning is accompanied by a human-readable reason</small>
      </div>
    </div>
  </div>

  <div class="col">
    <div class="card h-100">
      <div class="card-body">
        <h4 class="mb-2">Advisory</h4>
        <small>Risk guidance rather than definitive fraud accusations</small>
      </div>
    </div>
  </div>

  <div class="col">
    <div class="card h-100">
      <div class="card-body">
        <h4 class="mb-2">Cold-start Ready</h4>
        <small>Rules and zero-shot reasoning before sufficient labels exist</small>
      </div>
    </div>
  </div>
</div>

## The Problem

Online-classifieds platforms make local buying and selling highly accessible, but users often have limited information when deciding whether an advertisement deserves trust.

Potential buyers may encounter:

- unusually low or inconsistent prices,
- requests for advance payment,
- misleading or reused images,
- contradictions between the description and structured attributes,
- attempts to move communication outside the platform,
- unclear ownership or location information,
- and persuasive claims that are difficult to verify.

Conventional moderation systems primarily operate at the platform level. HOOSHYAR addresses a complementary problem: helping an individual user understand risk **at the moment of decision**.

The system is therefore positioned as a **risk and verification advisor**, not as a seller, guarantor, law-enforcement authority, or definitive fraud detector.

## User Journey

<div class="text-center my-4">
  <img
    src="{{ '/assets/img/projects/hooshyar/user-journey.png' | relative_url }}"
    alt="HOOSHYAR user journey from listing selection to an explainable safety report"
    class="img-fluid rounded z-depth-1"
  >
</div>

HOOSHYAR supports two deployment paths.

### Standalone Web MVP

In the initial version, the user pastes the URL of an online listing into the HOOSHYAR website.

The system:

1. extracts the listing token,
2. retrieves available listing information,
3. performs the multi-signal analysis,
4. and presents an advisory report on the HOOSHYAR interface.

This path enables early validation of the risk-analysis logic without requiring deep in-platform integration.

### Marketplace Viewer Add-on

In the integrated version, HOOSHYAR appears as a service available to a user viewing a listing.

The workflow is:

1. the user selects the HOOSHYAR service from the listing,
2. the marketplace redirects the user with a temporary listing token,
3. the backend retrieves the permitted listing data,
4. the analysis engine generates the risk report,
5. the user reviews explanations and recommendations,
6. and the completion flow returns the user to the marketplace.

The same backend and analysis core can support both deployment paths.

## Multi-signal Risk Analysis

<div class="text-center my-4">
  <img
    src="{{ '/assets/img/projects/hooshyar/risk-analysis.png' | relative_url }}"
    alt="HOOSHYAR multi-signal listing verification and explainable risk analysis"
    class="img-fluid rounded z-depth-1"
  >
</div>

The analysis combines heterogeneous signals rather than relying on a single classifier.

### Text and Claim Analysis

The system examines the Persian listing description for patterns such as:

- urgency and pressure language,
- deposit or advance-payment requests,
- requests to continue outside the platform,
- inconsistent product descriptions,
- unrealistic promises,
- missing critical details,
- and known high-risk linguistic patterns.

### Structured-data Consistency

Claims in the free-text description are compared with available structured fields.

Examples include:

- model or category mismatch,
- incompatible product characteristics,
- conflicting price information,
- location inconsistencies,
- and disagreement between seller claims and platform metadata.

### Image Analysis

The visual-analysis layer is designed to identify signals such as:

- duplicated or reused images,
- stock imagery,
- possible manipulation,
- inconsistency between images and listing claims,
- and visual characteristics that do not match the advertised item.

An image signal is treated as one source of evidence and is not independently interpreted as proof of fraud.

### Price Plausibility

The price module estimates whether the advertised price is plausible relative to comparable items and historical or offline reference data.

The system distinguishes between:

- a price within the expected range,
- a somewhat unusual price,
- a strongly anomalous price,
- and insufficient comparison data.

Unusual pricing contributes to the overall risk profile but does not determine the result by itself.

### Transaction and Communication Signals

The system also considers indicators such as:

- availability of platform-protected communication,
- requests to use external messaging,
- advance-payment language,
- urgency before inspection,
- business-verification information,
- and consistency of the listing location.

## Phased Detection Strategy

HOOSHYAR uses a staged development strategy to address the lack of high-quality fraud labels during the early phase of the project.

### Phase 1: Rule-based and Zero-shot Analysis

The first version combines:

- expert-designed heuristics,
- rule-based consistency checks,
- LLM zero-shot classification,
- agentic reasoning across multiple signals,
- and explainable aggregation.

This approach supports an operational MVP before a sufficiently large labeled dataset exists.

### Phase 2: Human-verified Learning Data

As the platform accumulates:

- verified reports,
- user feedback,
- expert-reviewed cases,
- transaction outcomes,
- and false-positive or false-negative corrections,

these signals can be converted into a controlled training dataset.

### Phase 3: Supervised Risk Models

Once sufficient verified data become available, supervised models can learn combinations of signals that are difficult to capture through manual rules alone.

The initial rules and LLM explanations can remain active as:

- interpretable features,
- fallback mechanisms,
- policy controls,
- and explanations for the learned model.

This hybrid roadmap reduces the cold-start barrier without treating early heuristic outputs as permanent ground truth.

## System Architecture

<div class="text-center my-4">
  <img
    src="{{ '/assets/img/projects/hooshyar/system-architecture.png' | relative_url }}"
    alt="High-level architecture of the HOOSHYAR risk-advisory platform"
    class="img-fluid rounded z-depth-1"
  >
</div>

The high-level architecture contains the following components.

### Listing Integration Layer

This layer:

- receives a listing URL or temporary listing token,
- validates the incoming request,
- retrieves authorized listing data,
- and returns the user through the required completion flow.

### Request and Cache Layer

Because external APIs may have strict request quotas, the system is designed to:

- cache listing data and completed analyses,
- avoid duplicate requests,
- reuse recent comparable-listing results,
- and separate offline reference-data generation from live user requests.

### Multi-signal Analysis Layer

The analysis layer coordinates:

- rule-based heuristics,
- Persian NLP,
- LLM zero-shot reasoning,
- structured-field validation,
- image inspection,
- reference-price analysis,
- and cross-signal consistency checking.

### Risk Aggregation Layer

The evidence produced by each component is combined into:

- an overall risk category,
- confidence or evidence sufficiency,
- positive signals,
- warning indicators,
- and unresolved uncertainties.

### Explanation and Advisory Layer

The final layer transforms technical signals into user-facing guidance.

It explains:

- which signals affected the assessment,
- why each signal matters,
- what remains uncertain,
- and what practical steps the user should take.

## Explainable Advisory Report

<div class="text-center my-4">
  <img
    src="{{ '/assets/img/projects/hooshyar/advisory-report.png' | relative_url }}"
    alt="Example HOOSHYAR explainable risk report and transaction-safety recommendations"
    class="img-fluid rounded z-depth-1"
  >
</div>

A report may include the following sections.

### Overall Assessment

The listing is assigned a cautious category such as:

```text
Low Risk
Moderate Risk
Elevated Risk
Insufficient Evidence
```

This category represents the detected indicators and available evidence. It is not a legal or factual judgment about the seller.

### Positive Signals

Examples may include:

- price within an expected reference range,
- consistency between the description and structured fields,
- availability of in-platform chat,
- recognizable business information,
- and images consistent with the listing.

### Warning Indicators

Examples may include:

- unusually low pricing,
- deposit requests,
- pressure to act quickly,
- communication outside the platform,
- inconsistent location or product information,
- repeated or stock images,
- and missing verification evidence.

### Recommended Actions

The system may recommend:

- inspecting the item in person,
- avoiding advance payments,
- verifying ownership and identity,
- retaining communication inside the marketplace,
- comparing the listing with similar items,
- and seeking specialist inspection for high-value purchases.

## Responsible Risk Communication

A central design requirement of HOOSHYAR is to avoid presenting uncertain model predictions as established facts.

The system does not state:

```text
This listing is fraudulent.
```

Instead, it communicates:

```text
This listing contains several indicators associated with elevated transaction risk.
```

This distinction is important for:

- legal and reputational safety,
- reducing harm from false positives,
- maintaining user trust,
- and communicating the limitations of AI-based assessments.

The report also explains that:

- the absence of warning signals does not guarantee safety,
- the presence of a signal does not prove malicious intent,
- incomplete data can reduce confidence,
- and users remain responsible for performing appropriate transaction checks.

## API and Operational Constraints

The system is designed for deployment under real-world platform limitations.

Important engineering considerations include:

- external API request quotas,
- restricted access to seller or comparable-listing information,
- authorization and user-consent boundaries,
- secure storage and rotation of API credentials,
- cache invalidation,
- timeout and failure handling,
- and graceful degradation when information is unavailable.

When a signal cannot be calculated reliably, the report marks it as unavailable rather than silently converting missing information into a negative score.

## User Feedback and Human Review

User and expert feedback provide an important mechanism for improving the system.

Potential feedback sources include:

- reporting an actual scam,
- marking a warning as useful or irrelevant,
- rating the final report,
- submitting transaction outcomes,
- and specialist review of ambiguous cases.

Feedback is not automatically treated as ground truth. It must be reviewed, deduplicated, and validated before being used for model training or policy updates.

## My Role

As the **AI/NLP engineer and system architect**, I contributed to:

- defining the end-to-end risk-advisory workflow,
- designing the phased cold-start and supervised-learning strategy,
- specifying the multi-signal risk-analysis architecture,
- designing rule-based and LLM zero-shot components,
- developing the explainable risk-aggregation approach,
- defining the platform add-on and token-based integration flow,
- designing the caching and API-efficiency strategy,
- establishing responsible and probabilistic output framing,
- defining user-facing warning and recommendation structures,
- and addressing legal, privacy, and reputational risks in the product design.

## Technology Stack

`Python` · `FastAPI` · `LLMs` · `Agentic Reasoning` · `Zero-shot Classification` · `Persian NLP` · `Rule-based Systems` · `Computer Vision` · `Redis` · `REST APIs` · `Risk Scoring` · `Explainable AI`

## Current Status

HOOSHYAR is an ongoing applied-AI project.

Current work focuses on:

- platform approval and integration,
- reliable access to listing and comparable-item data,
- calibration of rule weights,
- construction of safe reference-price data,
- design of the user-facing risk report,
- evaluation of false-positive risks,
- and preparation of a verified feedback pipeline.

No quantitative accuracy or fraud-detection claims are presented until a representative labeled evaluation set and controlled validation protocol are available.

## Design Principles

### Advisory, Not Accusatory

The system communicates risk indicators and uncertainty rather than issuing definitive accusations.

### Explain Before Scoring

Users should understand why a risk level was assigned, not merely receive a number.

### Multiple Signals, Not One Shortcut

No single price, text, image, or metadata feature should independently determine the final result.

### Missing Data Is Not Negative Evidence

Unavailable information must be represented as uncertainty, not automatically treated as suspicious.

### Safety Through Actionable Guidance

The value of the system lies not only in detecting risk but also in teaching users how to transact more safely.

## Project Significance

HOOSHYAR explores how AI can support safer marketplace decisions while respecting uncertainty, platform constraints, and the serious consequences of incorrect fraud accusations.

Its central contribution is the integration of explainable multi-signal analysis, agentic reasoning, responsible risk communication, and real-world marketplace deployment into a single user-centered advisory workflow.