---
layout: page
title: Collections
---
{% include breadcrumb.html %}
<ul>
  {% for collection in site.collections %}
    {% assign collection_name = collection.label %}
    {% for item in site[collection_name] %}
      <li>
        <h2>{{ item.title }}</h2>
        <p>{{ item.description }}</p>
        <p>{{ item.content }}</p>
      </li>
    {% endfor %}
  {% endfor %}
</ul>