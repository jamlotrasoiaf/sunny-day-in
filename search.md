---
layout: post
---
<div class="header-search">
  <form class="header-search-form" action="{{ site.url }}/search" method="get">
    <input type="text" id="search-box" name="query">
    <input type="submit" value="search">
  </form>
</div>

<ul id="search-results"></ul>

<script>
  window.store = {
    {% for post in site.posts %}
      "{{ post.url | slugify }}": {
        "title": "{{ post.title | xml_escape }}",
        "author": "{{ post.author | xml_escape }}",
        "excerpt": "{{ post.excerpt | xml_escape }}",
        "content": "{{ post.content | strip_html | strip_newlines | jsonify }}",
        "url": "{{ post.url | xml_escape }}"
      }
      {% unless forloop.last %},{% endunless %}
    {% endfor %}
  };
</script>
<script src="https://unpkg.com/lunr/lunr.js"></script>
<script src="/assets/js/search.js"></script>
