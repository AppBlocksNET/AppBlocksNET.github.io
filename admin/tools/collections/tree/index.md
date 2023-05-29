---
layout: page
breadcrumbs: AppBlocks.NET - Admin = Tools - Tree
title: Tree
menu: admin
---
{% include breadcrumb.html %}
<ul>
  {% assign current_path = page.url | remove: "/" | prepend: site.baseurl %}
  {% for file in site.pages %}
    {% assign file_url = file.url | remove: "/" | prepend: site.baseurl %}
    {% if file_url contains current_path %}
      {% assign remaining_path = file_url | remove: current_path | remove: '/' %}
      {% assign path_segments = remaining_path | split: '/' %}
      {% if path_segments.size > 1 %}
        {% assign folder = path_segments[1] %}
        {% if folder != '_site' and folder != '' %}
          <li><a href="{{ file_url }}">{{ folder }}</a></li>
        {% endif %}
      {% else %}
        {% assign file_name = path_segments[0] %}
        <li><a href="{{ file_url }}">{{ file_name }}</a></li>
      {% endif %}
    {% endif %}
  {% endfor %}
</ul>
