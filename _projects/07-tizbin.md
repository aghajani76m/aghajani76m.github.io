---
layout: page
title: TIZBIN
description: A social-media user-discovery and behavioral-intelligence platform for profile enrichment, activity analysis, relationship discovery, and model-assisted user insights.
img: assets/img/projects/tizbin/cover.png
importance: 3
category: applied-ai
---

<div class="text-center mb-4">
  <img
    src="{{ '/assets/img/projects/tizbin/cover.png' | relative_url }}"
    alt="TIZBIN social-media user discovery and behavioral-intelligence platform"
    class="img-fluid rounded z-depth-1"
  >
</div>

<div class="d-flex flex-wrap justify-content-center gap-2 mb-4">
  <span class="badge rounded-pill text-bg-primary px-3 py-2">
    Applied AI Platform
  </span>

  <span class="badge rounded-pill text-bg-light border px-3 py-2">
    User Intelligence
  </span>

  <span class="badge rounded-pill text-bg-light border px-3 py-2">
    Social-Media Analytics
  </span>

  <span class="badge rounded-pill text-bg-light border px-3 py-2">
    Persian NLP
  </span>
</div>

## Overview

**TIZBIN** is a social-media user-discovery and behavioral-intelligence platform designed to transform fragmented public social-media activity into structured, searchable, and analyzable user profiles.

The platform allows analysts to begin with a username, hashtag, topic, or behavioral filter and progressively move through several levels of analysis:

1. discovering potentially relevant accounts,
2. filtering users according to profile and activity properties,
3. inspecting a unified user profile,
4. analyzing temporal and behavioral patterns,
5. identifying related users and communities,
6. and extracting model-assisted insights.

TIZBIN combines large-scale data processing, Persian NLP, social-network analysis, profile enrichment, and interactive visual analytics in a single operational workflow.

<div class="row row-cols-1 row-cols-md-2 row-cols-lg-4 g-3 text-center my-4">
  <div class="col">
    <div class="card h-100">
      <div class="card-body">
        <h4 class="mb-2">Searchable</h4>
        <small>Discovery by username, hashtag, topic, and profile attributes</small>
      </div>
    </div>
  </div>

  <div class="col">
    <div class="card h-100">
      <div class="card-body">
        <h4 class="mb-2">Profile-centered</h4>
        <small>Unified views combining metadata, activity, and inferred signals</small>
      </div>
    </div>
  </div>

  <div class="col">
    <div class="card h-100">
      <div class="card-body">
        <h4 class="mb-2">Behavioral</h4>
        <small>Temporal, thematic, geographic, and relationship analysis</small>
      </div>
    </div>
  </div>

  <div class="col">
    <div class="card h-100">
      <div class="card-body">
        <h4 class="mb-2">Modular</h4>
        <small>Independent analytical services coordinated through scalable APIs</small>
      </div>
    </div>
  </div>
</div>

## The Problem

Information about a social-media user is usually distributed across many disconnected records.

A user may publish content over several months or years, participate in different topics, interact with multiple communities, change profile metadata, and use several languages or geographic references.

Basic platform search generally exposes only a small portion of this information. It does not provide a structured answer to questions such as:

- Which users are most relevant to a topic?
- How has an account's activity changed over time?
- Which hashtags, topics, or communities are associated with the account?
- Which other users exhibit similar behavior?
- Where is the user likely to be located?
- Is the account highly influential within a specific community?
- Which parts of a profile are observed directly, and which are model-generated estimates?

TIZBIN addresses this problem through a user-centered intelligence workflow that combines direct metadata, historical activity, network relationships, and machine-learning outputs.

## User Search and Discovery

<div class="text-center my-4">
  <img
    src="{{ '/assets/img/projects/tizbin/user-discovery.png' | relative_url }}"
    alt="TIZBIN user discovery, filtering, and search-results interface"
    class="img-fluid rounded z-depth-1"
  >
  <p class="text-muted small mt-2">
    Public portfolio images use anonymized accounts and generalized content.
  </p>
</div>

Users can begin an investigation using:

- a username,
- a hashtag,
- a topic,
- or a combination of advanced filters.

Search results are presented as profile cards containing a compact summary of each account.

Depending on the available data, a card may include:

- platform identifier,
- username and display name,
- available location information,
- content category,
- follower and following counts,
- post volume,
- account-creation date,
- and selected activity indicators.

The discovery interface also supports filtering according to properties such as:

- post count,
- follower count,
- estimated account age,
- account-creation period,
- platform,
- predicted content category,
- geographic attributes,
- and other profile or behavioral indicators.

This allows analysts to move beyond keyword search and construct a more precise candidate set.

## Unified User Profile

<div class="text-center my-4">
  <img
    src="{{ '/assets/img/projects/tizbin/profile-overview.png' | relative_url }}"
    alt="TIZBIN unified user profile and activity interface"
    class="img-fluid rounded z-depth-1"
  >
</div>

Selecting an account opens a unified profile that brings together the available information about that user.

The profile is organized into several analytical layers.

### Observed Profile Information

This layer contains information directly obtained from authorized source data, such as:

- display name,
- username,
- biography,
- profile and cover images,
- follower and following counts,
- account-creation date,
- available location text,
- and recent public content.

### Activity History

The activity section provides access to the user's historical posts and enables filtering according to:

- time,
- hashtags,
- activity type,
- post type,
- content,
- and search terms.

This allows analysts to inspect both individual posts and broader activity patterns.

### Advanced User Analysis

The advanced-analysis section summarizes model-generated and aggregated indicators, including:

- follower growth,
- content-production trends,
- active hours and days,
- frequently used hashtags,
- commonly used terms,
- related accounts,
- topic distribution,
- and geographic signals.

### Identity-resolution Support

When permitted by the use case and governance policy, the system can organize evidence relevant to account identity resolution.

Such evidence must be treated as probabilistic and investigative support rather than a definitive identification of a person.

## Behavioral Analytics

<div class="text-center my-4">
  <img
    src="{{ '/assets/img/projects/tizbin/behavior-analytics.png' | relative_url }}"
    alt="TIZBIN behavioral analytics including activity, follower growth, and temporal patterns"
    class="img-fluid rounded z-depth-1"
  >
</div>

TIZBIN converts user activity into multiple analytical views.

### Follower Growth

Time-series charts show how the follower count changes across the available observation period.

This can help reveal:

- gradual organic growth,
- sudden increases or decreases,
- campaign-related changes,
- and possible anomalies requiring further investigation.

A change in follower count is treated as an observed pattern, not by itself as evidence of manipulation.

### Content-production Growth

The system displays how frequently the user publishes content over time.

This makes it possible to compare:

- high-activity and low-activity periods,
- changes in publishing behavior,
- campaign-related bursts,
- and long-term activity consistency.

### Activity Heatmaps

Hourly and daily heatmaps identify the time periods in which an account is most active.

These visualizations can help analysts understand:

- regular posting schedules,
- unusual activity windows,
- changes in daily behavior,
- and differences between weekdays and weekends.

### Hashtag and Keyword Analysis

The system extracts frequent hashtags and terms from the user's public content.

These results can support:

- topic discovery,
- content summarization,
- campaign analysis,
- similarity analysis,
- and community detection.

Frequently used terms should always be interpreted in their original context rather than as definitive evidence of intent or affiliation.

## Model-assisted User Intelligence

<div class="text-center my-4">
  <img
    src="{{ '/assets/img/projects/tizbin/system-capabilities.png' | relative_url }}"
    alt="TIZBIN analytical microservices and user-intelligence capabilities"
    class="img-fluid rounded z-depth-1"
  >
</div>

TIZBIN uses specialized analytical services rather than a single monolithic classifier.

The service layer can support the following tasks.

### Similar-user Discovery

Accounts can be compared using signals such as:

- common hashtags,
- topic similarity,
- content embeddings,
- interaction patterns,
- shared communities,
- and behavioral features.

The output is a ranked list of potentially related users, not a claim that the accounts are controlled by the same person.

### Geographic Inference

When explicit location information is missing, the system may estimate geographic attributes from signals such as:

- biography and profile location,
- place names in content,
- language usage,
- time-zone behavior,
- known regional entities,
- and historical activity.

Possible outputs include estimated country and, for supported regions, province-level location.

These estimates are accompanied by uncertainty and must not be treated as verified residence information.

### User and Post Classification

Text-classification services can categorize:

- user activity,
- account interests,
- individual posts,
- and dominant content topics.

The classifier supports Persian-language categories such as:

- social,
- political,
- scientific and technological,
- economic,
- cultural and artistic,
- medical,
- and international content.

### Influential-user Detection

The system can identify highly active or potentially influential accounts within a selected topic or community.

Signals may include:

- content volume,
- interaction volume,
- network position,
- audience size,
- and participation in relevant conversations.

Influence remains context-dependent and cannot be reduced to follower count alone.

### Community and Relationship Clustering

Graph and similarity methods group users according to:

- interaction relationships,
- shared hashtags,
- common topics,
- co-participation,
- and behavioral similarity.

This capability supports the discovery of communities and related-account structures.

### Additional Profile Estimates

The platform architecture also supports model-assisted estimation of properties such as:

- approximate age group,
- gender presentation,
- account authenticity indicators,
- and likely account type.

These outputs are probabilistic estimates and may be inaccurate, especially when profile data are limited or deliberately misleading.

They require careful governance and should only be used in authorized, proportionate analytical contexts.

## Related Accounts and Content Insights

TIZBIN can connect an individual account to a broader analytical context.

The system may provide:

- related-account recommendations,
- interaction or similarity networks,
- frequently used hashtags,
- keyword clouds,
- topic distributions,
- content-category summaries,
- and comparative views between users.

These outputs help analysts move from a single profile toward an understanding of the surrounding community and content environment.

## System Architecture

The high-level architecture contains the following stages:

```text
Authorized Social Data
          ↓
Collection and Normalization
          ↓
Raw-data Processing
          ↓
Feature Extraction and Enrichment
          ↓
Specialized Analytical Services
          ↓
Processed Data Storage
          ↓
REST APIs
          ↓
Search, Profiles, Analytics, and Comparison
```

### Data Collection

Public or otherwise authorized social-media records are collected through platform integrations and controlled crawling components.

### Processing and Enrichment

Raw records are normalized and enriched with:

- consistent identifiers,
- extracted text features,
- language labels,
- topic labels,
- geographic indicators,
- temporal attributes,
- and relationship information.

### Specialized Services

Independent services perform:

- classification,
- geographic inference,
- user similarity,
- network analysis,
- clustering,
- keyword extraction,
- and profile aggregation.

### Storage and Retrieval

Processed records are stored in a search-oriented data infrastructure that supports:

- large historical collections,
- structured filtering,
- full-text search,
- aggregation,
- and near-real-time analytical queries.

### API and Presentation

REST APIs expose structured analytical results to the web interface.

The separation between data processing, intelligence services, storage, and presentation allows individual components to be updated or scaled independently.

## My Role

As an **AI/NLP engineer and data-infrastructure lead**, I contributed to:

- designing the user-discovery and profile-analysis workflow,
- developing high-throughput analytical APIs,
- implementing Persian text-processing and classification services,
- designing geographic-inference components,
- creating user and post classification datasets,
- implementing profile-enrichment pipelines,
- designing similar-user and clustering workflows,
- integrating behavioral and temporal analytics,
- optimizing Elasticsearch indexing and analytical queries,
- coordinating data-processing microservices,
- deploying and maintaining production-facing services,
- and translating analytical outputs into frontend-ready API responses.

## Technology Stack

`Python` · `FastAPI` · `Elasticsearch` · `Redis` · `Docker` · `REST APIs` · `PyTorch` · `Transformers` · `Scikit-learn` · `Persian NLP` · `Text Classification` · `Geolocation Detection` · `Social Network Analysis` · `Web Crawling` · `Data Visualization`

## Privacy and Responsible Use

User-intelligence systems involve significant privacy, fairness, and misuse risks.

TIZBIN therefore requires responsible-use principles such as:

- processing only legally and contractually authorized data,
- minimizing unnecessary personal-data exposure,
- restricting access according to user roles,
- distinguishing observed facts from model-generated estimates,
- exposing uncertainty and confidence where possible,
- avoiding irreversible decisions based solely on automated inference,
- regularly evaluating model bias,
- and maintaining logs for authorized analytical access.

Particular caution is required for:

- identity resolution,
- age and gender estimation,
- location inference,
- account-authenticity classification,
- and relationship or affiliation inference.

These outputs must be interpreted as analytical indicators, not verified personal facts.

## Public Portfolio Anonymization

The screenshots displayed on this page have been prepared for public presentation.

They do not intentionally expose:

- real usernames,
- profile photographs,
- personal biographies,
- private contact information,
- exact inferred identities,
- or sensitive post content.

Where necessary, original values are blurred, removed, or replaced by representative examples.

## Current Status

TIZBIN was developed as an implemented social-media analytics platform with:

- search and user discovery,
- advanced filtering,
- unified user profiles,
- behavioral analytics,
- temporal visualizations,
- keyword and hashtag analysis,
- related-user discovery,
- and modular intelligence services.

The current public portfolio page focuses on system design and engineering capabilities rather than presenting claims about individual users or unreleased model-performance results.

## Design Principles

### Observed Data and Inference Must Be Separated

The interface should clearly distinguish source metadata from estimated attributes.

### Analysis Should Remain Reviewable

Analysts must be able to inspect the evidence behind important conclusions.

### Similarity Does Not Imply Identity

Related behavior, common hashtags, or network proximity do not prove common ownership or coordination.

### Missing Data Represents Uncertainty

Incomplete profiles should not automatically be classified as suspicious or deceptive.

### Sensitive Inference Requires Proportionate Use

Location, identity, age, gender, and authenticity estimates require authorization, necessity, and human review.

## Project Significance

TIZBIN demonstrates how large-scale social-media records can be transformed into a user-centered intelligence environment combining search, profile enrichment, Persian NLP, behavioral analytics, social-network analysis, and scalable data infrastructure.

Its main contribution is the integration of these capabilities into a unified workflow that allows analysts to move from broad discovery to structured, reviewable, and context-aware user analysis.