---
layout: default
---
# Welcome
<div class="welcome">
<p>Welcome on my website. Feel free to browse.</p>

<p>You can go directly to the latest post here:</p>
{% for post in site.posts limit:1 %}
    <a href="{{ post.url }}">{{ post.title }} - <time datetime="{{ post.date | date_to_xmlschema }}" itemprop="datePublished">{{ post.date | date: "%B %d, %Y" }}</time></a>
{% endfor %}
</div>

<div class="cat-list">
<h2>Categories</h2>
<p>Use the links below to jump directly to the category in the list:</p>
{% assign categories_list = site.categories %}
  {% if categories_list.first[0] == null %}
    {% for category in categories_list %}
      <a href="#{{ category }}" class="cat-item">{{ category | capitalize }} ({{ site.tags[category].size }})</a>
    {% endfor %}
  {% else %}
    {% for category in categories_list %}
      <a href="#{{ category[0] | downcase }}" class="cat-item">{{ category[0] | capitalize }} ({{ category[1].size }})</a>
    {% endfor %}
  {% endif %}
{% assign categories_list = nil %}
</div>

<div class="post-list">
<h2>List of posts</h2>
{% for category in site.categories %}
  <h3 class="cat-name" id="{{ category[0] }}">{{ category[0] | capitalize }}</h3>
  <ul>
    {% assign pages_list = category[1] %}
    {% for post in pages_list %}
      {% if post.title != null %}
      {% if group == null or group == post.group %}
      <li><a href="{{ site.url }}{{ post.url }}">{{ post.title }} - <time datetime="{{ post.date | date_to_xmlschema }}" itemprop="datePublished">{{ post.date | date: "%B %d, %Y" }}</time></a></li>
      {% endif %}
      {% endif %}
    {% endfor %}
    {% assign pages_list = nil %}
    {% assign group = nil %}
  </ul>
{% endfor %}
</div>
