---
layout: page
breadcrumbs: AppBlocks.NET - Admin - Tools - Html_Pages - List
title: Html_Pages - List
menu: admin
---

{% for page in site.html_pages %}
  [{{ page.title }}]({{ page.url | absolute_url }})
{% endfor %}
