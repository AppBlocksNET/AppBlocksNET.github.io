---
layout: page
---
{% for file in site.static_files %}
  [{{ file.title }}]({{ file.path | absolute_url }})
{% endfor %}
