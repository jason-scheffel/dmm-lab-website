---
title: Research
nav:
  order: 2
  tooltip: Research projects
---

# {% include icon.html icon="fa-solid fa-microscope" %}Research Projects

{% assign projects = site.research | sort: "order" %}
{% for project in projects %}
  {% include research-project.html project=project %}
{% endfor %}
