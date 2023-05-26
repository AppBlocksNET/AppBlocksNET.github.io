---
layout: page
---
<ul>
  {% for key in site %}
    <li>
      <strong>{{ key }}</strong>
      {% assign value = site[key] %}
      {% if value != null %}
        {% if value.size > 0 %}
          <ul>
            {% for subkey in value %}
              <li>
                {% if subkey == "html_pages" %}
                  <strong>{{ subkey }}</strong>
                  <ul>
                    {% for page in site.html_pages %}
                      <li>
                        <strong>Page:</strong>
                        <ul>
                          {% for pageKey in page %}
                            <li>
                              <strong>{{ pageKey }}</strong>: {{ page[pageKey] }}
                            </li>
                          {% endfor %}
                        </ul>
                      </li>
                    {% endfor %}
                  </ul>
                {% else %}
                  <strong>{{ subkey }}</strong>: {{ subvalue }}
                {% endif %}
              </li>
            {% endfor %}
          </ul>
        {% else %}
          <em>No data</em>
        {% endif %}
      {% else %}
        <em>No value</em>
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
