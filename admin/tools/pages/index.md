---
layout: page
breadcrumbs: AppBlocks.NET - Admin - Tools - Pages
title: Pages
menu: admin
---
{% include breadcrumb.html %}
{% for page in site.pages %}
  [{{ page.title }}]({{ page.url | absolute_url }})
{% endfor %}
