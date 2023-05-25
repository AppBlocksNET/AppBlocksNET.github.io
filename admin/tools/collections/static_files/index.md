---
layout: page
---
{% for file in site.static_files %}
  [{{ file.name }}]({{ file.path | absolute_url }})
{% endfor %}
