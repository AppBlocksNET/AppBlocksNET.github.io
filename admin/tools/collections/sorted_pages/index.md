---
layout: page
breadcrumbs: AppBlocks.NET - Admin - Tools - Sorted_Pages
title: Sorted_Pages
menu: admin
---
{% include breadcrumb.html %}
{% assign sorted_pages = site.pages | sort: 'url' | where_exp: 'page', 'page.url != "/assets/"' %}
{% for page in sorted_pages %}
  [{{ page.title }}]({{ page.url | absolute_url }})
{% endfor %}
