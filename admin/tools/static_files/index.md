---
layout: page
breadcrumbs: AppBlocks.NET - Admin - Tools - Static_Files
title: Static_Files
menu: admin
---
{% include breadcrumb.html %}
{% for file in site.static_files %}
  [{{ file.name }}]({{ file.path | absolute_url }})
{% endfor %}
