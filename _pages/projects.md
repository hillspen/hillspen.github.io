---
layout: page
title: projects
permalink: /projects/
description: Some cool projects.
nav: true
nav_order: 3
display_categories: #
horizontal: false
---

<!-- pages/projects.md -->
<div class="projects">
{% if site.enable_project_categories and page.display_categories %}
  <!-- Display categorized projects -->
  {% for category in page.display_categories %}
  <a id="{{ category }}" href=".#{{ category }}">
    <h2 class="category">{{ category }}</h2>
  </a>
  {% assign categorized_projects = site.projects | where: "category", category %}
  {% assign sorted_projects = categorized_projects | sort: "importance" %}
  <!-- Generate cards for each project -->
  {% if page.horizontal %}
  <div class="container">
    <div class="row row-cols-1 row-cols-md-2">
    {% for project in sorted_projects %}
      {% include projects_horizontal.liquid %}
    {% endfor %}
    </div>
  </div>
  {% else %}
  <div class="row row-cols-1 row-cols-md-3">
    {% for project in sorted_projects %}
      {% include projects.liquid %}
    {% endfor %}
  </div>
  {% endif %}
  {% endfor %}

{% else %}

<!-- Display projects without categories -->

{% assign sorted_projects = site.projects | sort: "importance" %}

  <!-- Generate cards for each project -->

{% if page.horizontal %}

  <div class="container">
    <div class="row row-cols-1 row-cols-md-2">
    {% for project in sorted_projects %}
      {% include projects_horizontal.liquid %}
    {% endfor %}
    </div>
  </div>
  {% else %}
  <div class="row row-cols-1 row-cols-md-3">
    {% for project in sorted_projects %}
      {% include projects.liquid %}
    {% endfor %}
  </div>
  {% endif %}
{% endif %}
</div>

<!-- Modal -->
<div class="modal fade" id="projectModal" tabindex="-1" role="dialog" aria-labelledby="projectModalLabel" aria-hidden="true">
  <div class="modal-dialog modal-lg" role="document">
    <div class="modal-content">
      <div class="modal-header">
        <h5 class="modal-title" id="projectModalLabel"></h5>
        <button type="button" class="close" data-dismiss="modal" aria-label="Close">
          <span aria-hidden="true">&times;</span>
        </button>
      </div>
      <div class="modal-body" id="projectModalBody">
        <!-- Project details will go here -->
      </div>
    </div>
  </div>
</div>

<script>
document.addEventListener('DOMContentLoaded', function() {
  document.querySelectorAll('.project-card').forEach(function(card) {
    card.addEventListener('click', function() {
      var projectId = card.getAttribute('data-project-id');
      var projectData = window.projectsData[projectId];
      if (projectData) {
        document.getElementById('projectModalLabel').textContent = projectData.title;
        document.getElementById('projectModalBody').innerHTML = projectData.html;
        $('#projectModal').modal('show');
      }
    });
  });
});
</script>

<script>
window.projectsData = {
  {% for project in site.projects %}
    "{{ project.slug }}": {
      "title": {{ project.title | jsonify }},
      "html": {{ project.content | markdownify | jsonify }}
    }{% unless forloop.last %},{% endunless %}
  {% endfor %}
};
</script>
