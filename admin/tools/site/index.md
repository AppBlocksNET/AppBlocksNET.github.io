---
layout: page
---
<ul>
  {% for key in site %}
    <li>
      <strong>{{ key }}</strong>
      {% assign value = site[key] %}
      {% if value != null and value != empty %}
        <ul>
          {% for subkey in value %}
            <li>
              <strong>{{ subkey }}</strong>
              {% assign subvalue = value[subkey] %}
              {% if subvalue != null and subvalue != empty %}
                <ul>
                  {% for subsubkey in subvalue %}
                    <li>
                      <strong>{{ subsubkey }}</strong>: {{ subvalue[subsubkey] }}
                    </li>
                  {% endfor %}
                </ul>
              {% endif %}
            </li>
          {% endfor %}
        </ul>
      {% else %}
        <em>No data</em>
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
