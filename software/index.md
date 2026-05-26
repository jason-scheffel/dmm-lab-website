---
title: Software
nav:
  order: 5
  tooltip: Software and code
redirect_from:
  - /code.html
---

# {% include icon.html icon="fa-solid fa-code" %}Software

{% assign software_items = site.software | where_exp: "item", "item.hidden != true" | sort: "order" %}
{% for software in software_items %}
  {% include software-item.html software=software %}
{% endfor %}
