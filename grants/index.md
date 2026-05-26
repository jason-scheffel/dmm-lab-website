---
title: Grants
nav:
  order: 3
  tooltip: Research funding
redirect_from:
  - /funding.html
  - /funding.html/
---

# {% include icon.html icon="fa-solid fa-hand-holding-dollar" %}Grants

## Current Funding

{% assign current_grants = site.grants | where: "status", "current" | where_exp: "grant", "grant.hidden != true" | sort: "order" %}
{% for grant in current_grants %}
  {% include grant.html grant=grant %}
{% endfor %}

{% include section.html %}

## Past Funding

{% assign past_grants = site.grants | where: "status", "past" | where_exp: "grant", "grant.hidden != true" | sort: "order" %}
{% for grant in past_grants %}
  {% include grant.html grant=grant %}
{% endfor %}
