---
layout: default
---
{% assign sorted_pages = site.pages | sort: 'url' | where_exp: 'page', 'page.url != "/assets/"' %}
{% for page in sorted_pages %}
  [{{ page.title }}]({{ page.url | absolute_url }})
{% endfor %}
