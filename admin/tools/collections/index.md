---
layout: page
pagetitle: Collections
title: Collections
---
<ul>
  {% assign current_path = page.url | remove: "/" %}
  {% for file in site.static_files %}
    {% assign file_path = file.path | remove: "/" %}
    {% if file_path contains current_path %}
      {% assign remaining_path = file_path | remove: current_path %}
      {% if remaining_path != file_path %}
        {% assign folder = remaining_path | split: "/" | first %}
        {% if folder != '_site' and folder != '' %}
          <li><a href="{{ remaining_path }}">{{ folder }}</a></li>
        {% endif %}
      {% else %}
        {% assign file_name = file_path | split: "/" | last %}
        <li><a href="{{ remaining_path }}">{{ file_name }}</a></li>
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