---
layout: page
title: Projects
permalink: /projects/
description: Selected research, applied AI, and data-engineering projects by Mohammad Aghajani Asl.
nav: true
nav_order: 2
horizontal: false
---

<p class="lead">
  A selection of my research and engineering work in trustworthy AI,
  agentic AI, Persian NLP, intelligent systems, and large-scale data infrastructure.
</p>

<div class="projects">

  <section id="research-projects" class="mb-5">
    <h2 class="project-section-title">Research Projects</h2>
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
    <h2 class="project-section-title">Applied AI Systems</h2>
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
    <h2 class="project-section-title">Data Engineering & Infrastructure</h2>  
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
<style>
  .project-section-title {
    margin: 3rem 0 1.25rem;
    padding-bottom: 0.6rem;
    border-bottom: 1px solid var(--global-divider-color);
    color: var(--global-text-color) !important;
    font-size: 2rem;
    font-weight: 500;
    line-height: 1.25;
    text-align: left !important;
    opacity: 1 !important;
  }

@media (max-width: 576px) {
.project-section-title {
margin-top: 2.25rem;
margin-bottom: 1rem;
font-size: 1.65rem;
}
}
</style>
