---
layout: home
pagetitle: Sitemap
title: Sitemap
menu: main
---
<!-- {% for page in site.pages | where_exp: 'page', 'page.title' | sort: 'page.url' %}
  [{{ page.title }}]({{ site.url }}{{ page.url | remove: "index.html" }})
{% endfor %} -->
{% assign sorted_pages = site.pages | sort: 'url' %}

{% assign sorted_pages = site.pages | sort: 'url' %}

<ul>
  {% for page in sorted_pages %}
    {% assign url_parts = page.url | split: '/' %}
    {% assign url_parts_size = url_parts | size %}
    {% assign rm = url_parts | last %}
    {% assign base_url = page.url | replace: rm, '' %}
    
    {% assign is_root_page = url_parts_size == 1 %}
    {% assign parent_folder = base_url | split: '/' | last %}
    {% assign is_child_page = parent_folder != '' %}
    
    {% if is_root_page %}
      <li><a href="{{ page.url }}">{{ page.title }}</a></li>
    {% endif %}
    
    {% if is_child_page %}
      {% capture nested_ul_id %}nested_ul_{{ parent_folder }}{% endcapture %}
      
      {% if forloop.first %}
        <li>
          <a href="{{ page.url }}">{{ page.title }}</a>
          <ul id="{{ nested_ul_id }}">
      {% endif %}
      
      {% if forloop.last or page.url | split: '/' | last == 'index.html' %}
        <li><a href="{{ page.url }}">{{ page.title }}</a></li>
      {% endif %}
      
      {% if forloop.last or page.url | split: '/' | last == 'index.html' %}
          </ul>
        </li>
      {% endif %}
    {% endif %}
  {% endfor %}
</ul>

