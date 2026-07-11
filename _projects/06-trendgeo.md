---
layout: page
title: TRENDGEO
description: A geospatial social-media intelligence platform for detecting, mapping, analyzing, and comparing regional and multilingual trends.
img: assets/img/projects/trendgeo/cover.png
importance: 2
category: applied-ai
---

<div class="text-center mb-4">
  <img
    src="{{ '/assets/img/projects/trendgeo/cover.png' | relative_url }}"
    alt="TRENDGEO geospatial social-media trend intelligence platform"
    class="img-fluid rounded z-depth-1"
  >
</div>

<div class="d-flex flex-wrap justify-content-center gap-2 mb-4">
  <span class="badge rounded-pill text-bg-primary px-3 py-2">
    Production System
  </span>

  <span class="badge rounded-pill text-bg-light border px-3 py-2">
    Social-Media Analytics
  </span>

  <span class="badge rounded-pill text-bg-light border px-3 py-2">
    Geospatial Intelligence
  </span>

  <span class="badge rounded-pill text-bg-light border px-3 py-2">
    Multilingual NLP
  </span>
</div>

## Overview

**TRENDGEO** is a geospatial social-media intelligence platform designed to detect, map, analyze, and compare emerging trends across countries, provinces, languages, and online communities.

The platform transforms high-volume social-media streams into structured analytical views by processing content according to:

- geographic location,
- language,
- publication time,
- media type,
- topic,
- sentiment,
- hashtags,
- and user activity.

Its outputs are presented through interactive maps, trend lists, temporal charts, geographic distributions, content-analysis panels, hashtag graphs, word clouds, influential-user reports, and side-by-side comparison workspaces.

TRENDGEO was designed to support both rapid situational awareness and deeper investigation of how narratives emerge, concentrate geographically, and spread between regions.

<div class="row row-cols-2 row-cols-md-4 g-3 text-center my-4">
  <div class="col">
    <div class="card h-100">
      <div class="card-body">
        <h3 class="mb-1">12</h3>
        <small>Active processing and trend services at handover</small>
      </div>
    </div>
  </div>

  <div class="col">
    <div class="card h-100">
      <div class="card-body">
        <h3 class="mb-1">5</h3>
        <small>Language-specific geolocation pipelines</small>
      </div>
    </div>
  </div>

  <div class="col">
    <div class="card h-100">
      <div class="card-body">
        <h3 class="mb-1">6</h3>
        <small>Trend-extraction service scopes</small>
      </div>
    </div>
  </div>

  <div class="col">
    <div class="card h-100">
      <div class="card-body">
        <h3 class="mb-1">Multi-level</h3>
        <small>World, country, province, language, and region analysis</small>
      </div>
    </div>
  </div>
</div>

## The Problem

Social-media trends can emerge and evolve within very short time windows.

A hashtag, news story, video, or coordinated narrative may:

- become dominant in one province,
- spread to neighboring regions,
- cross language boundaries,
- appear differently across platforms,
- and involve different communities at different stages.

Simple trend lists cannot explain this process. They show what is popular, but often fail to show:

- where the activity is concentrated,
- when it accelerated,
- which languages and media formats dominate,
- which users or communities are involved,
- and how two trends or regions differ.

TRENDGEO addresses this limitation by combining trend detection with geographic, temporal, content, and user-level analysis.

## Interactive Geographic Exploration

<div class="text-center my-4">
  <img
    src="{{ '/assets/img/projects/trendgeo/interactive-map.png' | relative_url }}"
    alt="TRENDGEO interactive geographic map and regional trend exploration"
    class="img-fluid rounded z-depth-1"
  >
</div>

The main interface provides a geographic overview of active trends.

Users can begin with a global or regional map and progressively move toward a selected country, province, region, or hashtag.

The map experience supports:

- displaying important trends across geographic areas,
- showing frequently occurring hashtags at different locations,
- selecting a time interval,
- navigating from an overview to a focused regional analysis,
- and accessing related tweets, users, and analytical panels.

Selecting a geographic region changes the system from a general monitoring view into a focused analytical workspace.

For the selected area, the system can display:

- dominant hashtags,
- hashtag rank and activity volume,
- important or influential posts,
- temporal activity,
- and related users.

## Data Processing Pipeline

<div class="text-center my-4">
  <img
    src="{{ '/assets/img/projects/trendgeo/data-pipeline.png' | relative_url }}"
    alt="TRENDGEO multilingual data processing and geographic trend-extraction pipeline"
    class="img-fluid rounded z-depth-1"
  >
</div>

The end-to-end processing workflow contains several major layers.

### 1. Social-Media Data Collection

Raw content is collected and transferred from supported social-media sources.

The production architecture includes dedicated processing for Twitter/X data and a separate transfer process for Facebook data.

### 2. Normalization and Language Separation

Incoming records are cleaned, standardized, and separated according to their detected or recorded language.

Dedicated pipelines were implemented for:

- Persian,
- Arabic,
- Hebrew,
- Turkish,
- and Urdu.

### 3. Geographic Enrichment

Language-specific transport services do more than copy records between indexes.

Before transfer, each record is processed to estimate or assign geographic labels such as:

- country,
- province,
- and other available location attributes.

For records associated with Iran, the pipeline can also perform province-level enrichment when sufficient evidence is available.

### 4. Language-specific Monthly Indexing

Geographically enriched records are stored in monthly, language-specific indexes.

This organization supports:

- scalable querying,
- time-range filtering,
- separation of language-specific workloads,
- maintenance of large historical collections,
- and efficient analytical aggregation.

### 5. Trend Extraction

Separate services identify trends across different analytical scopes.

The supported extraction scopes include:

- global trends,
- trends across all countries,
- a selected country,
- language-specific trends,
- trends across all provinces,
- and a selected province.

This architecture allows the same platform to support both macro-level and local analysis.

### 6. Backend and Analytical APIs

The backend receives frontend requests, applies filters, executes analytical queries, prepares chart-ready datasets, and returns standardized responses.

The API layer separates complex data processing from the user interface and allows the analytical features to be reused across multiple pages.

### 7. Interactive Presentation

The frontend transforms the analytical responses into maps, charts, tables, cards, graphs, word clouds, and comparison panels.

## Operational Service Architecture

At the time of project handover, twelve principal services were active.

They covered two main groups.

### Data Preparation and Transport

- Facebook data transfer
- Persian tweet geographic enrichment and transfer
- Arabic tweet geographic enrichment and transfer
- Hebrew tweet geographic enrichment and transfer
- Turkish tweet geographic enrichment and transfer
- Urdu tweet geographic enrichment and transfer

### Trend Extraction

- global trend extraction
- all-country trend extraction
- selected-country trend extraction
- language-based trend extraction
- all-province trend extraction
- selected-province trend extraction

Separating the services by task and analytical scope makes the system easier to operate, monitor, restart, and extend.

## Hashtag Analytics

<div class="text-center my-4">
  <img
    src="{{ '/assets/img/projects/trendgeo/hashtag-analytics.png' | relative_url }}"
    alt="TRENDGEO hashtag content, temporal, geographic, and user analytics dashboard"
    class="img-fluid rounded z-depth-1"
  >
</div>

The hashtag-analysis workspace combines several complementary perspectives.

### General Activity Indicators

The platform can summarize indicators such as:

- total number of posts,
- reposts,
- replies,
- likes,
- views,
- estimated reach,
- and number of participating users.

It can also expose the dominant:

- content category,
- topic,
- language,
- sentiment,
- and media type.

### Temporal Analysis

Time-series charts show how a trend changes over the selected period.

This helps analysts identify:

- the initial emergence of a trend,
- sudden activity spikes,
- sustained attention,
- declining engagement,
- and differences between organic and highly concentrated activity patterns.

### Content Analysis

The content-analysis panels help explain what is being discussed around a hashtag.

Outputs may include:

- frequently occurring words,
- related hashtags,
- hashtag graphs,
- word clouds,
- dominant topics,
- dominant media formats,
- frequent accounts,
- and narrative-oriented content summaries.

### User and Geographic Analysis

The user-analysis view examines active accounts according to dimensions such as:

- country and province,
- account type,
- account age,
- activity level,
- verification status,
- posting frequency,
- and geographic participation.

This allows analysts to examine which regions and user groups contribute most strongly to a trend.

### Posts and Media

A searchable list provides access to relevant posts and associated media.

Available filters can include:

- geographic area,
- time range,
- language,
- media type,
- hashtag,
- and analytical categories.

## Comparative Intelligence

<div class="text-center my-4">
  <img
    src="{{ '/assets/img/projects/trendgeo/comparison-workspace.png' | relative_url }}"
    alt="TRENDGEO side-by-side comparison of hashtags, trends, and geographic regions"
    class="img-fluid rounded z-depth-1"
  >
</div>

The advanced comparison workspace allows analysts to compare two or more hashtags or geographic areas in parallel.

Comparison dimensions include:

- number of posts,
- reposts,
- replies,
- likes,
- views,
- reach,
- participating users,
- temporal activity,
- geographic distribution,
- dominant content,
- dominant topic,
- dominant language,
- user-account categories,
- activity categories,
- and influential or highly active accounts.

This capability is useful for:

- comparing competing narratives,
- measuring regional differences,
- examining how the same event is discussed in different locations,
- identifying different participating communities,
- and assessing whether two trends have similar or distinct patterns of propagation.

## Advanced Search and Filtering

TRENDGEO provides advanced search for analysts who need to construct a precise subset of the available data.

Filters can be combined across dimensions such as:

- date and time range,
- geographic location,
- language,
- hashtag,
- platform or media type,
- user attributes,
- content category,
- and activity indicators.

The same filtering concepts are applied consistently across maps, charts, post lists, user analytics, and comparison pages.

## Product Differentiation

Many public trend websites primarily provide ranked lists of popular hashtags at a global or national level.

TRENDGEO extends this model by combining:

- province-level and country-level geographic analysis,
- Persian and regional-language support,
- content and sentiment analysis,
- user-distribution analysis,
- multilingual pipelines,
- advanced comparison,
- and direct access to underlying posts and media.

The objective is not simply to show what is trending, but to help analysts understand the structure, geography, timing, and participants behind the trend.

## My Role

My work on TRENDGEO included responsibilities across AI/NLP, backend engineering, data infrastructure, product coordination, and final delivery.

I contributed to:

- designing and maintaining the multilingual data-processing workflow,
- developing geographic-enrichment and location-labeling components,
- implementing and operating language-specific transport services,
- designing trend-extraction services for multiple geographic scopes,
- developing analytical backend APIs and query workflows,
- preparing chart-ready and comparison-ready data,
- coordinating product requirements across data, backend, frontend, and user-experience work,
- reviewing analytical pages and filters,
- supporting production deployment and service operation,
- and preparing the technical handover and maintenance documentation.

## Technology Stack

`Python` · `FastAPI` · `Elasticsearch` · `REST APIs` · `Microservices` · `Docker` · `Social-Media Analytics` · `Persian NLP` · `Multilingual NLP` · `Geolocation Detection` · `Sentiment Analysis` · `Topic Classification` · `Data Visualization`

## Privacy and Responsible Use

Geospatial and social-media analytics may affect individuals and communities, particularly when content is interpreted without sufficient context.

Responsible operation therefore requires:

- relying on data that the platform is authorized to process,
- avoiding unnecessary exposure of personal information,
- separating aggregate analysis from claims about individuals,
- documenting model and geolocation uncertainty,
- restricting sensitive analytical capabilities to authorized users,
- and interpreting trends as observed activity rather than definitive evidence of public opinion or intent.

Location predictions and automated classifications should be treated as analytical estimates rather than guaranteed facts.

## Current Status

TRENDGEO reached an operational handover stage with:

- active multilingual data-processing services,
- geographic labeling and transfer pipelines,
- multiple trend-extraction scopes,
- analytical backend APIs,
- an interactive map interface,
- hashtag and user analytics,
- advanced filtering,
- and a comparative-analysis workspace.

The project was documented to support future maintenance, service monitoring, data updates, and extension of the analytical capabilities.

## Project Significance

TRENDGEO demonstrates how large-scale social-media streams can be converted into a structured geospatial intelligence environment.

Its contribution lies in combining multilingual NLP, geographic enrichment, trend detection, scalable indexing, backend analytics, and interactive visual exploration within one end-to-end production platform.