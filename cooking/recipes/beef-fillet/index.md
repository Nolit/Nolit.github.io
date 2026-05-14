---
layout: default
title: Beef fillet
---

# Index

<ul>
{% assign current_dir = page.dir %}
{% assign pages_in_dir = site.pages | where: "dir", current_dir | sort: "name" %}

{% for p in pages_in_dir %}
  {% unless p.name == "index.md" %}
    <li>
      <a href="{{ p.url | relative_url }}">{{ p.title | default: p.name }}</a>
    </li>
  {% endunless %}
{% endfor %}
</ul>