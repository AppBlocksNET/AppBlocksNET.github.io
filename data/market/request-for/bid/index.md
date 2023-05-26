---
layout: home 
breadcrumbs: AppBlocks.NET - Market - Request For Bid
pagetitle: Request For Bid
title: Request For Bid
menu: main
---
<ul>
  {% assign current_path = page.url | remove: "/" | prepend: site.baseurl %}
  {% for file in site.static_files %}
    {% assign file_path = file.path | remove: "/" | prepend: site.baseurl %}
    {% if file_path contains current_path %}
      {% assign remaining_path = file_path | remove: current_path | remove: '/' %}
      {% assign path_segments = remaining_path | split: '/' %}
      {% if path_segments.size > 1 %}
        {% assign folder = path_segments[1] %}
        {% if folder != '_site' and folder != '' %}
          <li><a href="{{ file_path }}">{{ folder }}</a></li>
        {% endif %}
      {% else %}
        {% assign file_name = path_segments[0] %}
        <li><a href="{{ file_path }}">{{ file_name }}</a></li>
      {% endif %}
    {% endif %}
  {% endfor %}
</ul>
