---
layout: home
pagetitle: Sitemap
title: Sitemap
menu: main
---
{% for page in site.pages %}
  <a href="{{ site.url }}{{ page.url | remove: "index.html" }}">
    {% if page.date %}
      {{ page.date | date_to_xmlschema }}
    {% else %}
      {{ site.time | date_to_xmlschema }}
    {% endif %}
    {{ page.title }}</a><br/>
{% endfor %}
