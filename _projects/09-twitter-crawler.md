---
layout: page
title: TWITTER_CRAWLER
description: A scalable and recoverable social-data ingestion infrastructure for collecting, normalizing, enriching, and indexing large continuously updated Twitter/X datasets.
img: assets/img/projects/twitter-crawler/cover.png
importance: 2
category: data-infrastructure
---

<div class="text-center mb-4">
  <img
    src="{{ '/assets/img/projects/twitter-crawler/cover.png' | relative_url }}"
    alt="TWITTER_CRAWLER scalable social-data ingestion infrastructure"
    class="img-fluid rounded z-depth-1"
  >
</div>

<div class="d-flex flex-wrap justify-content-center gap-2 mb-4">
  <span class="badge rounded-pill text-bg-primary px-3 py-2">
    Data Infrastructure
  </span>

  <span class="badge rounded-pill text-bg-light border px-3 py-2">
    Distributed Ingestion
  </span>

  <span class="badge rounded-pill text-bg-light border px-3 py-2">
    Incremental Collection
  </span>

  <span class="badge rounded-pill text-bg-light border px-3 py-2">
    Search Infrastructure
  </span>
</div>

## Overview

**TWITTER_CRAWLER** is a scalable social-data ingestion and indexing infrastructure designed to maintain large historical and continuously updated Twitter/X datasets.

The system collects public or otherwise authorized records, converts heterogeneous platform responses into a consistent internal schema, enriches the records with analytical metadata, and prepares them for full-text search, aggregation, NLP processing, trend detection, and user-level analysis.

The project was designed as a complete operational pipeline rather than a single-purpose crawler.

Its major capabilities include:

- distributed task scheduling,
- incremental synchronization,
- cursor and checkpoint persistence,
- retry and backoff control,
- duplicate-safe processing,
- conversation and repost relation extraction,
- schema normalization,
- bulk Elasticsearch indexing,
- and operational monitoring.

The public portfolio intentionally emphasizes architecture, reliability, and engineering capability rather than exact collection volumes, account counts, tokens, credentials, or internal source lists.

<div class="row row-cols-1 row-cols-md-2 row-cols-lg-4 g-3 text-center my-4">
  <div class="col">
    <div class="card h-100">
      <div class="card-body">
        <h4 class="mb-2">Distributed</h4>
        <small>Independent workers coordinated through persistent task state</small>
      </div>
    </div>
  </div>

  <div class="col">
    <div class="card h-100">
      <div class="card-body">
        <h4 class="mb-2">Incremental</h4>
        <small>Only newly available records are synchronized after each cursor</small>
      </div>
    </div>
  </div>

  <div class="col">
    <div class="card h-100">
      <div class="card-body">
        <h4 class="mb-2">Recoverable</h4>
        <small>Interrupted tasks resume without reprocessing complete histories</small>
      </div>
    </div>
  </div>

  <div class="col">
    <div class="card h-100">
      <div class="card-body">
        <h4 class="mb-2">Analytics-ready</h4>
        <small>Normalized events support search, NLP, graphs, and trend analysis</small>
      </div>
    </div>
  </div>
</div>

## The Engineering Challenge

Large-scale social-data collection presents several challenges that are absent from small ad hoc scripts.

A production pipeline must handle:

- continuously changing timelines,
- multiple source and query types,
- pagination and cursor state,
- edits and deletions,
- temporary service failures,
- changing metadata,
- duplicate events,
- rate constraints,
- network instability,
- and downstream indexing pressure.

A naive implementation may repeatedly collect the same records, lose cursor state after failure, create inconsistent schemas, or overload the search infrastructure.

TWITTER_CRAWLER addresses these problems through a persistent, distributed, and idempotent design.

## High-level Architecture

<div class="text-center my-4">
  <img
    src="{{ '/assets/img/projects/twitter-crawler/system-architecture.png' | relative_url }}"
    alt="High-level distributed architecture of the Twitter/X data-ingestion system"
    class="img-fluid rounded z-depth-1"
  >
</div>

The architecture contains several independent layers.

### Source Registry

The source registry stores collection definitions such as:

- public account or source identifier,
- query or hashtag definition,
- collection mode,
- synchronization status,
- previous cursor,
- scheduling policy,
- and authorization metadata.

Collection workers do not rely on hard-coded source lists.

### Scheduler and Task Queue

The scheduler converts source definitions into executable collection tasks.

It manages:

- task priority,
- source synchronization frequency,
- duplicate-task prevention,
- retry timing,
- and worker assignment.

### Collector Workers

Workers execute collection tasks independently.

Depending on the task type, a worker may collect:

- posts,
- user metadata,
- reply relations,
- repost relations,
- quote relations,
- hashtags,
- mentions,
- media metadata,
- and incremental updates.

The collection layer can integrate multiple permitted acquisition methods while exposing one normalized output contract to downstream components.

### Validation and Normalization

Platform responses are validated and converted into a stable internal schema.

This shields downstream applications from changes in external response formats.

### Checkpoint and Cursor Management

Every task maintains recoverable progress.

Cursor state may represent:

- the latest processed post,
- a pagination token,
- a time window,
- or a completed historical segment.

### Storage and Search

Raw and normalized records are stored separately when required.

Processed events are indexed in Elasticsearch for analytical use.

### API and Monitoring Layer

Backend APIs expose query, aggregation, and NLP-ready data.

Monitoring components report system health, task state, lag, indexing latency, and failures.

## Collection Lifecycle

<div class="text-center my-4">
  <img
    src="{{ '/assets/img/projects/twitter-crawler/collection-lifecycle.png' | relative_url }}"
    alt="Incremental social-data collection, cursor persistence, and retry lifecycle"
    class="img-fluid rounded z-depth-1"
  >
</div>

Each task follows a controlled lifecycle.

### 1. Source or Query Registration

A public account, hashtag, topic, or authorized query is registered with a collection policy.

### 2. Task Creation

The scheduler creates a task only when the source is eligible for synchronization.

This prevents unnecessary concurrent collection for the same source.

### 3. Cursor Loading

The worker loads the most recent successfully persisted position.

### 4. Incremental Retrieval

The worker requests only the records not previously completed.

This reduces:

- repeated network traffic,
- duplicate processing,
- storage cost,
- and downstream index updates.

### 5. Validation and Normalization

Malformed or incomplete objects are handled explicitly.

Accepted records are converted into the internal data model.

### 6. Duplicate Detection

Stable platform identifiers and source-aware keys prevent duplicate indexing when:

- a task is retried,
- cursor windows overlap,
- multiple collection methods return the same event,
- or a worker restarts.

### 7. Cursor Persistence

Progress is persisted in small increments to minimize the amount of work lost during interruption.

### 8. Indexing and Rescheduling

Accepted records are indexed, and the source is scheduled for its next synchronization.

## Normalized Data Model

The internal schema can represent:

- post identifier,
- author identifier,
- timestamp,
- text,
- detected language,
- reply target,
- repost source,
- quote source,
- hashtags,
- mentions,
- media metadata,
- engagement counters,
- public profile metadata,
- collection provenance,
- and processing status.

Conversation and propagation relations are stored explicitly to support graph-based analysis.

The model distinguishes:

- observed source attributes,
- collection metadata,
- and model-generated analytical features.

## Relationship Extraction

A major advantage of the normalized pipeline is that it preserves relationships between records.

These relationships include:

- reply chains,
- repost relationships,
- quote-post relationships,
- hashtag co-occurrence,
- mention networks,
- and author-to-topic participation.

This structure supports downstream applications such as:

- diffusion analysis,
- community detection,
- influential-user identification,
- coordinated-activity research,
- and narrative propagation analysis.

Relationship similarity or proximity is not interpreted as definitive evidence of coordination or common ownership.

## Reliability and Observability

<div class="text-center my-4">
  <img
    src="{{ '/assets/img/projects/twitter-crawler/reliability-observability.png' | relative_url }}"
    alt="Reliability, checkpointing, rate-aware scheduling, and monitoring controls"
    class="img-fluid rounded z-depth-1"
  >
</div>

The infrastructure includes several controls for stable operation.

### Retry with Backoff

Temporary failures are retried using increasing delays.

Permanent failures and invalid collection definitions are separated from recoverable errors.

### Rate-aware Scheduling

The scheduler responds to service limits and availability signals by delaying or redistributing work.

The objective is stable and policy-aware execution, not circumvention of restrictions.

### Credential Isolation

Credentials and authentication material are separated from task payloads and logs.

Workers receive only the minimum configuration required for authorized execution.

### Fault Isolation

A failure in one source or worker does not halt unrelated tasks.

### Persistent Cursors

Workers can recover after process restarts, deployment updates, or temporary service interruption.

### Idempotent Processing

Reprocessing the same event produces the same final indexed state.

### Backpressure

When storage or indexing slows down, the ingestion rate is reduced to prevent uncontrolled queue growth.

### Monitoring

Operational metrics can include:

- queued and active tasks,
- collection lag,
- recent completions,
- retry counts,
- source-level errors,
- worker heartbeats,
- cursor age,
- indexing latency,
- and failed batches.

## Indexing Pipeline

<div class="text-center my-4">
  <img
    src="{{ '/assets/img/projects/twitter-crawler/indexing-pipeline.png' | relative_url }}"
    alt="Twitter/X event normalization, relationship extraction, and Elasticsearch indexing pipeline"
    class="img-fluid rounded z-depth-1"
  >
</div>

The indexing process includes:

1. schema normalization,
2. text cleanup,
3. timestamp standardization,
4. hashtag and mention parsing,
5. reply, repost, and quote relation extraction,
6. duplicate detection,
7. provenance attachment,
8. partition routing,
9. and controlled bulk indexing.

Time-partitioned or source-aware index strategies support:

- large historical datasets,
- efficient date-range queries,
- scalable aggregation,
- retention policies,
- and maintenance operations.

The resulting search infrastructure supports:

- full-text search,
- hashtag analysis,
- language filtering,
- user profiling,
- conversation analysis,
- geographic enrichment,
- sentiment and topic classification,
- and trend extraction.

## Integration with Downstream NLP

Collected records feed several analytical pipelines.

Potential downstream tasks include:

- Persian language detection,
- sentiment classification,
- topic classification,
- geographic inference,
- named-entity recognition,
- bot or account-type analysis,
- trend extraction,
- and user-profile enrichment.

The crawler stores raw observable attributes separately from inferred model outputs so that models can be retrained without repeating collection.

## Scaling Strategy

The system scales horizontally by separating:

- source state,
- task state,
- worker execution,
- indexing,
- and analytical serving.

Additional workers can be added without manually partitioning the complete source list.

The main scaling principles are:

- centralized task coordination,
- persistent cursors,
- stateless or minimally stateful workers,
- batch-oriented storage operations,
- independently scalable indexing,
- and partition-aware source processing.

The public project page does not disclose exact throughput, account quantities, token counts, or infrastructure topology.

## Responsible Data Collection

The system is intended for public, authorized, and policy-compliant research and analytical use.

Responsible operation requires:

- processing only data the project is permitted to access,
- following applicable platform terms and law,
- avoiding unnecessary personal-data retention,
- restricting access to collected records,
- documenting provenance,
- defining retention and deletion procedures,
- and separating aggregate analysis from claims about individuals.

Technical accessibility is not treated as automatic permission for unrestricted collection.

## Public Portfolio Disclosure

The following details are intentionally excluded from the public portfolio:

- exact record volume,
- exact account or credential count,
- API keys and tokens,
- authentication configuration,
- internal query lists,
- server addresses,
- index names,
- proxy or networking details,
- operational thresholds,
- and recovery playbooks.

These details are not required to assess the engineering contribution and may create unnecessary security or compliance risks.

## My Role

As the **AI/NLP engineer and data-infrastructure lead**, I contributed to:

- designing the distributed social-data ingestion architecture,
- implementing task scheduling and worker coordination,
- developing incremental synchronization and cursor persistence,
- implementing duplicate-safe event processing,
- designing normalized post, user, and relationship schemas,
- integrating collected records with Elasticsearch,
- optimizing bulk indexing and analytical queries,
- preparing data for Persian NLP and user-intelligence systems,
- implementing monitoring and failure reporting,
- supporting production deployment,
- and documenting operational and data-processing workflows.

## Technology Stack

`Python` · `AsyncIO` · `FastAPI` · `Elasticsearch` · `Redis` · `Docker` · `Task Queues` · `Distributed Workers` · `Checkpointing` · `Social Network Analysis` · `Persian NLP` · `Structured Logging`

## Project Significance

TWITTER_CRAWLER demonstrates the engineering required to convert continuously changing social-media streams into stable, normalized, searchable, and analytically useful data.

Its main contribution is the integration of distributed ingestion, incremental synchronization, relationship extraction, duplicate-safe indexing, operational recovery, and downstream NLP readiness within one maintainable infrastructure.