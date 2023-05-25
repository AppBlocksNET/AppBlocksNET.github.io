---
layout: page
---
<ul>
  {% for item in site %}
    <li>
      {{ item[0] }}
      {% if item[1] %}
        <ul>
          {% for subitem in item[1] %}
            <li>{{ subitem[0] }}</li>
          {% endfor %}
        </ul>
      {% endif %}
    </li>
  {% endfor %}
</ul>

<ul>
  {% assign current_site = site | jsonify %}
  {% for node in current_site %}
    <li><a href="{{ node.path }}">{{ node.name }}</a>
      {% if node.children > 1 %} 

       </li>
      {% if path_segments.size > 1 %}
        {% assign folder = path_segments[1] %}
        {% if folder != '_site' and folder != '' %}
          <li><a href="{{ file_url }}">{{ folder }}</a></li>
        {% endif %}
      {% else %}
        {% assign file_name = path_segments[0] %}
        <li><a href="{{ file_url }}">{{ file_name }}</a></li>
      {% endif %}
    {% endif %}
  {% endfor %}
</ul>
