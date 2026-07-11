---
layout: page
title: Large-scale Persian NLP & Data Infrastructure
description: An end-to-end data and model infrastructure for constructing Persian-language datasets, training NLP models, and deploying production services for sentiment, topic, and geolocation analysis.
img: assets/img/projects/persian-nlp-infrastructure/cover.png
importance: 3
category: data-infrastructure
---

<div class="text-center mb-4">
  <img
    src="{{ '/assets/img/projects/persian-nlp-infrastructure/cover.png' | relative_url }}"
    alt="Large-scale Persian NLP and data infrastructure"
    class="img-fluid rounded z-depth-1"
  >
</div>

<div class="d-flex flex-wrap justify-content-center gap-2 mb-4">
  <span class="badge rounded-pill text-bg-primary px-3 py-2">
    Persian NLP
  </span>

  <span class="badge rounded-pill text-bg-light border px-3 py-2">
    Dataset Engineering
  </span>

  <span class="badge rounded-pill text-bg-light border px-3 py-2">
    Model Fine-tuning
  </span>

  <span class="badge rounded-pill text-bg-light border px-3 py-2">
    Production ML
  </span>
</div>

## Overview

**Large-scale Persian NLP & Data Infrastructure** is an end-to-end platform for transforming heterogeneous Persian social-media data into curated datasets, trained language models, scalable APIs, and production analytical services.

The project was developed to support Persian-language intelligence capabilities required by systems such as user profiling, trend analysis, geographic analytics, content exploration, and large-scale search.

Its scope extended beyond model training and included the complete machine-learning lifecycle:

- data collection and sampling,
- Persian text normalization,
- annotation and label quality control,
- dataset versioning,
- transformer fine-tuning,
- evaluation and error analysis,
- API development,
- containerized deployment,
- inference monitoring,
- and integration with large Elasticsearch-backed applications.

<div class="row row-cols-1 row-cols-md-2 row-cols-lg-4 g-3 text-center my-4">
  <div class="col">
    <div class="card h-100">
      <div class="card-body">
        <h3 class="mb-1">250K+</h3>
        <small>Annotated and training samples across Persian NLP tasks</small>
      </div>
    </div>
  </div>

  <div class="col">
    <div class="card h-100">
      <div class="card-body">
        <h3 class="mb-1">3+</h3>
        <small>Core model families for sentiment, topic, and geolocation</small>
      </div>
    </div>
  </div>

  <div class="col">
    <div class="card h-100">
      <div class="card-body">
        <h3 class="mb-1">~90%</h3>
        <small>Internal Persian sentiment evaluation accuracy</small>
      </div>
    </div>
  </div>

  <div class="col">
    <div class="card h-100">
      <div class="card-body">
        <h4 class="mb-2">Production</h4>
        <small>Containerized models integrated with operational systems</small>
      </div>
    </div>
  </div>
</div>

## The Problem

Persian NLP systems face several challenges that are less visible in high-resource languages.

These challenges include:

- limited availability of high-quality labeled datasets,
- inconsistent spelling and Unicode representation,
- informal social-media language,
- code-switching,
- dialectal variation,
- ambiguous geographic references,
- imbalanced topic distributions,
- limited benchmark coverage,
- and substantial domain shift between training and production data.

Training a model on a single static dataset is therefore insufficient.

Reliable Persian-language services require a repeatable infrastructure that can:

1. collect representative data,
2. construct and revise labels,
3. detect quality problems,
4. train and evaluate new model versions,
5. deploy the models safely,
6. and monitor their behavior on changing production data.

## End-to-end Dataset Pipeline

<div class="text-center my-4">
  <img
    src="{{ '/assets/img/projects/persian-nlp-infrastructure/dataset-pipeline.png' | relative_url }}"
    alt="End-to-end Persian NLP dataset construction and quality-control pipeline"
    class="img-fluid rounded z-depth-1"
  >
</div>

The dataset pipeline was designed as a reproducible process rather than a collection of manually edited files.

### 1. Data Selection

Candidate Persian records were sampled from authorized internal or public data collections.

Sampling strategies were adapted to the task.

Examples include:

- topic-balanced sampling,
- sentiment-rich keyword sampling,
- location-related profile sampling,
- temporal sampling,
- and uncertainty-based selection from an existing model.

The objective was to create representative datasets rather than simply selecting the most frequent records.

### 2. Persian Text Normalization

Social-media text contains many surface-level inconsistencies.

The normalization process handled issues such as:

- Arabic and Persian character variants,
- half-spaces,
- duplicated whitespace,
- URLs,
- mentions,
- hashtags,
- emoji,
- repeated characters,
- control characters,
- malformed Unicode,
- and platform-specific markup.

Original text was preserved when required so that normalization decisions remained reversible.

### 3. Duplicate and Near-duplicate Removal

Duplicate records can inflate evaluation results and bias the model toward frequently repeated content.

The pipeline therefore considered:

- exact text duplication,
- reposted content,
- normalized-text equality,
- near-duplicate similarity,
- and cross-split leakage.

Source-aware identifiers were retained to preserve provenance while preventing duplicated training examples.

### 4. Candidate Labeling

Labels were produced using combinations of:

- existing structured metadata,
- dictionaries and deterministic rules,
- previously trained classifiers,
- model-assisted annotation,
- and human review.

Automatically proposed labels were treated as candidates rather than unquestioned ground truth.

### 5. Human Review

Ambiguous, low-confidence, or strategically important samples were reviewed or corrected manually.

Review guidelines defined:

- the meaning of each class,
- positive and negative examples,
- treatment of mixed or ambiguous records,
- and conditions under which a sample should be excluded.

### 6. Dataset Balancing

Real-world distributions are often highly imbalanced.

The dataset-building workflow used techniques such as:

- controlled downsampling,
- targeted minority-class sampling,
- class weighting,
- and task-specific augmentation.

The objective was not to force every class to have identical size, but to provide sufficient coverage for reliable evaluation and learning.

### 7. Split Construction

Training, validation, and test sets were created with attention to:

- source separation,
- temporal leakage,
- duplicated users or posts,
- topic overlap,
- and geographic overlap.

Dataset splits were versioned so that model experiments could be reproduced.

## Persian NLP Task Suite

<div class="text-center my-4">
  <img
    src="{{ '/assets/img/projects/persian-nlp-infrastructure/nlp-task-suite.png' | relative_url }}"
    alt="Persian NLP model suite for sentiment, topic, and geographic analysis"
    class="img-fluid rounded z-depth-1"
  >
</div>

The infrastructure supported several complementary NLP tasks.

## Sentiment and Emotion Analysis

The sentiment service classifies the general affective orientation of Persian text.

Depending on the application and model version, outputs can include categories such as:

```text
Positive
Neutral
Negative
Mixed or Uncertain
```

The underlying dataset included examples from informal and noisy Persian social-media content.

Important challenges included:

- sarcasm,
- indirect sentiment,
- political or cultural context,
- emoji-dependent meaning,
- mixed positive and negative language,
- and neutral news-like statements.

A Persian sentiment model achieved approximately **90% accuracy in its task-specific internal evaluation**.

This number represents the reported evaluation under the project’s own dataset and split. It should not be interpreted as guaranteed accuracy across every Persian domain or platform.

## Topic Classification

The topic-classification service assigns broad semantic categories to Persian content.

Representative classes include:

- political,
- social,
- economic,
- scientific and technological,
- cultural and artistic,
- medical,
- religious,
- sports,
- and international content.

The model was used to enrich search and analytical records, enabling:

- topic filtering,
- trend summaries,
- user-interest analysis,
- content distribution charts,
- and comparative analytics.

Multi-topic or ambiguous content can be represented through confidence scores or a fallback category rather than being forced into a misleading class.

## Geographic Inference

The geolocation service estimates the likely geographic context associated with a user or record.

Depending on the available evidence, outputs can include:

- country,
- province,
- or unknown / insufficient evidence.

Potential signals include:

- profile location text,
- place names in biography or posts,
- language and dialect features,
- regional entities,
- time-related behavior,
- and previously observed geographic metadata.

Geolocation output is an estimate and not verified residence information.

Each prediction should be accompanied by:

- confidence,
- evidence coverage,
- and an unknown option.

For users associated with Iran, a second-stage model can estimate province-level location when sufficient evidence is available.

## Language and Content Enrichment

Supporting services enrich raw records with information such as:

- detected language,
- normalized text,
- extracted hashtags,
- mentions,
- named entities,
- media type,
- and model-processing status.

These attributes provide a common analytical layer for downstream search and dashboards.

## Model Development Lifecycle

<div class="text-center my-4">
  <img
    src="{{ '/assets/img/projects/persian-nlp-infrastructure/model-development.png' | relative_url }}"
    alt="Persian NLP model training, evaluation, error analysis, and release lifecycle"
    class="img-fluid rounded z-depth-1"
  >
</div>

The model-development process followed a controlled sequence.

### Baseline Development

Before fine-tuning larger transformer models, simpler baselines were established using methods such as:

- TF-IDF,
- logistic regression,
- linear support-vector machines,
- and conventional tree-based models where appropriate.

Baselines provided a transparent reference point and helped identify whether increased model complexity was justified.

### Transformer Fine-tuning

Persian and multilingual transformer models were fine-tuned using task-specific datasets.

Training considered:

- class imbalance,
- sequence length,
- learning rate,
- batch size,
- early stopping,
- and checkpoint selection.

### Evaluation

Evaluation went beyond overall accuracy.

Depending on the task, metrics included:

- Macro F1,
- per-class precision and recall,
- confusion matrices,
- geographic-level accuracy,
- coverage,
- and confidence calibration.

Macro-level metrics were important because a high-frequency class could otherwise dominate the overall score.

### Error Analysis

Incorrect predictions were grouped according to causes such as:

- ambiguous labels,
- annotation inconsistency,
- sarcasm,
- insufficient context,
- rare entities,
- code-switching,
- geographic-name ambiguity,
- and domain shift.

The findings were used to improve both the dataset and the model.

### Model Versioning

Every production candidate was associated with:

- dataset version,
- preprocessing configuration,
- training parameters,
- evaluation report,
- model artifact,
- and release status.

This made it possible to compare versions and roll back deployments when necessary.

## Production Architecture

<div class="text-center my-4">
  <img
    src="{{ '/assets/img/projects/persian-nlp-infrastructure/production-architecture.png' | relative_url }}"
    alt="Production architecture for Persian NLP models and analytical services"
    class="img-fluid rounded z-depth-1"
  >
</div>

The production infrastructure separates model training from online serving.

### Data Layer

Large Elasticsearch collections provide the source and destination for analytical records.

The data layer supports:

- full-text search,
- batch selection,
- aggregation,
- model-status filtering,
- and writing enrichment results back to processed indexes.

### Batch Inference

Batch workers process historical or newly indexed records.

Batch workflows are appropriate for:

- large-scale enrichment,
- backfilling new model outputs,
- reprocessing after model upgrades,
- and offline analytical jobs.

### Online APIs

FastAPI services provide online inference for applications requiring immediate predictions.

The APIs expose structured request and response contracts and can support:

- single-record inference,
- controlled batch inference,
- health checks,
- model-version information,
- and confidence values.

### Caching

Redis can be used to avoid repeated inference for unchanged records and to reduce response latency.

### Containerization

Model services are packaged with Docker to keep:

- model dependencies,
- preprocessing code,
- runtime libraries,
- and deployment configuration

consistent across development and production environments.

### Monitoring

Operational monitoring covers:

- API latency,
- request failures,
- batch throughput,
- queue backlog,
- model-loading status,
- prediction distributions,
- and data-processing lag.

Sudden shifts in predicted class distributions can indicate data drift, pipeline failure, or a new real-world event requiring inspection.

## Integration with Analytical Products

The model infrastructure was designed to serve multiple applications rather than one isolated interface.

Outputs can support systems such as:

- social-media trend analysis,
- geographic trend mapping,
- user profiling,
- advanced search,
- content filtering,
- comparative dashboards,
- and recommendation of related records.

A common enrichment schema allows several applications to consume the same model outputs consistently.

## Data and Model Quality

Production model quality depends on more than the neural architecture.

The project therefore emphasized:

- annotation guidelines,
- representative sampling,
- duplicate control,
- split integrity,
- class-level evaluation,
- error categorization,
- and feedback from downstream users.

A model with a high aggregate metric can still be unsuitable if it systematically fails on a minority class, region, dialect, or topic.

## Responsible Use

Several model outputs involve sensitive inferences.

Particular care is required for:

- geographic inference,
- sentiment interpretation,
- user-interest classification,
- and analysis of social or political content.

Responsible operation requires:

- processing only authorized data,
- distinguishing observed metadata from inferred attributes,
- exposing confidence and uncertainty,
- supporting an unknown class,
- avoiding irreversible decisions based solely on model output,
- evaluating bias across classes and regions,
- and limiting access to sensitive analytical results.

Geolocation and user-topic predictions must be interpreted as probabilistic analytical signals rather than verified personal facts.

## Public Portfolio Disclosure

The public project page does not disclose:

- private datasets,
- annotation-user identities,
- internal Elasticsearch index names,
- server addresses,
- credentials,
- sensitive geographic records,
- private source lists,
- or model artifacts that cannot be released.

Aggregate dataset size and task-level results are presented only to demonstrate engineering scale and model-development experience.

## My Role

As the **AI/NLP engineer and data-infrastructure lead**, I contributed to:

- designing the Persian NLP data lifecycle,
- constructing and quality-controlling large labeled datasets,
- developing Persian normalization and preprocessing pipelines,
- training sentiment, topic, and geolocation models,
- designing evaluation and error-analysis workflows,
- implementing batch and online inference services,
- developing high-throughput FastAPI endpoints,
- integrating model outputs with Elasticsearch,
- containerizing and deploying NLP services,
- monitoring production inference workflows,
- and maintaining model and dataset versions.

## Technology Stack

`Python` · `PyTorch` · `Transformers` · `Scikit-learn` · `Pandas` · `NumPy` · `FastAPI` · `Elasticsearch` · `Redis` · `Docker` · `Kibana` · `CI/CD` · `Index Lifecycle Management`

## Project Significance

This project demonstrates the complete transition from raw Persian social-media data to production-ready language-intelligence services.

Its contribution is not a single classifier, but an integrated data-centric infrastructure covering dataset creation, annotation, transformer training, evaluation, scalable serving, Elasticsearch integration, and responsible operational use.