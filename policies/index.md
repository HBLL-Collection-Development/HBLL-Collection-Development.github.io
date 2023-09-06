---
title: Collection Development Policies
---
{% comment %}
  https://github.com/kelsin/kelsin.github.io/blob/master/tags/index.html
{% endcomment %}

<div id="funds" name="funds">
  <h1>Fund Code</h1>

  {% capture posts %}
    {% for post in site.posts %}
      {% unless forloop.first %}|{% endunless %}{{ post.fund }}&mdash;{{ post.fund-name }}#{{ post.url }}
    {% endfor %}
  {% endcapture %}
  {% assign sortedposts = posts | lstrip | split: '|' | sort %}
  <ul>
  {% for post in sortedposts %}{% assign postitems = post | split: '#' %}
    <li><a href="{{ site.github.url }}{{ postitems[1] }}">{{ postitems[0] }}</a></li>
  {% endfor %}
  </ul>
</div>
