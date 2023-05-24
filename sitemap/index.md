---
layout: home 
breadcrumbs: AppBlocks.NET - Sports - Basketball - Leages
pagetitle: Sports
title: Sports
menu: main
---
{% for page in site.pages %}
  <a href="{{ site.url }}{{ page.url | remove: "index.html" }}{{ page.title }}</a>
    {% if page.date %}
      {{ page.date | date_to_xmlschema }} updated
    {% else %}
      {{ site.time | date_to_xmlschema }} updated
    {% endif %}
  <br/>
{% endfor %}
