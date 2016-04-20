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
  {% assign sortedposts = posts | split: '|' | sort %}
  <ul>
  {% for post in sortedposts %}{% assign postitems = post | split: '#' %}
    <li><a href="{{ site.github.url }}{{ postitems[1] }}">{{ postitems[0] }}</a></li>
  {% endfor %}
  </ul>
</div>

<div class="col" id="librarians" name="librarians">
  <h1>Librarian</h1>

  {% capture tagString %}{% for tag in site.tags %}{% assign slug = tag[0] | downcase | replace: ' ', '-' %}{{ site.data.librarians[slug].last-name}}#{{ site.data.librarians[slug].first-name}}#{{ slug }}#{{ tag[0] }}{% unless forloop.last %}|{% endunless %}{% endfor %}{% endcapture %}
  {% assign tags = tagString | split: '|' | sort %}
  {% for tag in tags %}
  {% assign slug = tag | split: '#' %}
  {% assign label = slug[3] %}
  {% assign slug = slug[2] %}
  <div class="tag">
    <a class="anchor" id="{{ slug }}"></a>
    <h3{% if forloop.first %} class="first"{% endif %}><a href="http://lib.byu.edu/directory/{{ slug }}/">{{ label }}</a></h3>
    {% capture posts %}{% for post in site.tags[label] %}{% unless forloop.first %}|{% endunless %}{{ post.fund }}&mdash;{{ post.fund-name }}#{{ post.url }}{% endfor %}{% endcapture %}
    {% assign sortedposts = posts | split: '|' | sort %}
    <ul>
    {% for post in sortedposts %}{% assign postitems = post | split: '#' %}
      <li><a href="{{ site.github.url }}{{ postitems[1] }}">{{ postitems[0] }}</a></li>
    {% endfor %}
    </ul>
  </div>
  {% endfor %}
</div>





