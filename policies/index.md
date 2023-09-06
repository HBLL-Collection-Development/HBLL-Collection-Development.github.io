---
title: Collection Development Policies
---
{% comment %}
  https://github.com/kelsin/kelsin.github.io/blob/master/tags/index.html
{% endcomment %}

<h1 class="small">Table of Contents</h1>
<ol class="small">
  <li><a href="#funds">Policies by Fund Code</a></li>
  <li><a href="#librarians">Policies by Librarian Name</a></li>
</ol>

<div class="col" id="funds" name="funds">
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
