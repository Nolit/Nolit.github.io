---
layout: default
title: Recipes
---

# Recipes

{% assign current_parts = page.path | split: "/" %}
{% assign current_filename = current_parts | last %}
{% assign current_dir = page.path | remove: current_filename %}

{% assign subdirs = "" | split: "" %}

{% for p in site.pages %}
  {% if p.path != page.path %}
    {% assign p_path = p.path %}

    {% if p_path contains current_dir %}
      {% assign relative_path = p_path | remove_first: current_dir %}
      {% assign relative_parts = relative_path | split: "/" %}

      {% if relative_parts.size > 1 %}
        {% assign subdir = relative_parts[0] %}

        {% unless subdirs contains subdir %}
          {% assign subdirs = subdirs | push: subdir %}
        {% endunless %}
      {% endif %}
    {% endif %}
  {% endif %}
{% endfor %}

<ul>
{% assign sorted_subdirs = subdirs | sort %}
{% for dir in sorted_subdirs %}
  <li>
    <a href="{{ page.dir | append: dir | append: '/' | relative_url }}">{{ dir }}</a>
  </li>
{% endfor %}
</ul>