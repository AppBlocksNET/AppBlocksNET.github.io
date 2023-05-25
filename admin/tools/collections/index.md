---
layout: page
pagetitle: Collections
title: Collections
---

<h1>{{ page.title }}</h1>

<ul>
  {% for file in site.static_files %}
    {% assign file_url = file.path | relative_url %}
    {% if file_url contains page.url %}
      {% assign file_path = file_url | remove: page.url %}
      {% assign file_segments = file_path | split: '/' %}
      {% if file_segments.size > 1 %}
        {% assign folder = file_segments[1] %}
        {% if folder != '_site' and folder != '' %}
          <li>{{ folder }}</li>
        {% endif %}
      {% else %}
        {% assign file_name = file_path | split: '/' | last %}
        <li>{{ file_name }}</li>
      {% endif %}
    {% endif %}
  {% endfor %}
</ul>

<ul>
  {% for collection in site.collections %}
    {% assign collection_name = collection.label %}
    {% for item in site[collection_name] %}
      <li>
        <h2>{{ item.title }}</h2>
        <p>{{ item.description }}</p>
        <p>{{ item.content }}</p>
      </li>
    {% endfor %}
  {% endfor %}
</ul>