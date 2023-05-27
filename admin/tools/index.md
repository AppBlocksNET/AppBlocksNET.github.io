---
layout: page
pagetitle: Tools
title: Tools
---
<ul>
  <li>[Collections](collections)
    <li>[Sorted_Pages](collections/sorted_pages)</li>
    <li>[Tree](collections/tree)</li>
  </li>
  <li>[Debug](debug)</li>
  <li>[Pages](pages)</li>
  <li>[Site](site)</li>
  <li>[Static_Files](static_files)</li>
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