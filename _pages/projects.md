---
layout: page
title: Projects
permalink: /projects/
description: Selected research, applied AI, and data-engineering projects by Mohammad Aghajani Asl.
nav: true
nav_order: 3
horizontal: false
---

<p class="lead">
  A selection of my research and engineering work in trustworthy AI,
  agentic RAG, Persian NLP, intelligent systems, and large-scale data infrastructure.
</p>

<div class="projects">

  <section id="research-projects" class="mb-5">
    <h2 class="category">Research Projects</h2>

    <p class="text-muted">
      Academic and research-oriented projects focused on trustworthy AI,
      multi-hop reasoning, question answering, and evidence-grounded generation.
    </p>

    {% assign research_projects = site.projects
      | where: "category", "research"
      | sort: "importance"
    %}

    <div class="row row-cols-1 row-cols-md-2 g-4">
      {% for project in research_projects %}
        {% include projects.liquid %}
      {% endfor %}
    </div>
  </section>

  <hr class="my-5">

  <section id="applied-ai-systems" class="mb-5">
    <h2 class="category">Applied AI Systems</h2>

    <p class="text-muted">
      End-to-end AI systems designed for real-world users, operational constraints,
      decision support, and intelligent product experiences.
    </p>

    {% assign applied_projects = site.projects
      | where: "category", "applied-ai"
      | sort: "importance"
    %}

    <div class="row row-cols-1 row-cols-md-2 g-4">
      {% for project in applied_projects %}
        {% include projects.liquid %}
      {% endfor %}
    </div>
  </section>

  <hr class="my-5">

  <section id="data-engineering-infrastructure" class="mb-5">
    <h2 class="category">Data Engineering & Infrastructure</h2>

    <p class="text-muted">
      Large-scale crawling, indexing, dataset construction, model training,
      and production data infrastructure for Persian-language AI systems.
    </p>

    {% assign infrastructure_projects = site.projects
      | where: "category", "data-infrastructure"
      | sort: "importance"
    %}

    <div class="row row-cols-1 row-cols-md-2 g-4">
      {% for project in infrastructure_projects %}
        {% include projects.liquid %}
      {% endfor %}
    </div>
  </section>

</div>