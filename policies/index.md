---
title: Collection Development Policies
---
{% comment %}
  https://github.com/kelsin/kelsin.github.io/blob/master/tags/index.html
{% endcomment %}

<h1>Funds</h1>


{% capture posts %}{% for post in site.posts %}{% unless forloop.first %}|{% endunless %}{{ post.title }}#{{ post.url }}{% endfor %}{% endcapture %}
{% assign sortedposts = posts | split: '|' | sort %}
<ul>
{% for post in sortedposts %}{% assign postitems = post | split: '#' %}
  <li><a href="{{ site.github.url }}{{ postitems[1] }}">{{ postitems[0] }}</a></li>
{% endfor %}
</ul>

<h1>Librarians</h1>

{% capture tagString %}{% for tag in site.tags %}{{ tag[0] }}{% unless forloop.last %}|{% endunless %}{% endfor %}{% endcapture %}
{% assign tags = tagString | split: '|' | sort %}

{% for tag in tags %}
{% assign slug = tag | downcase | replace: ' ', '_' %}
<div class="tag">
  <a class="anchor" id="{{ slug }}"></a>
  <h3>{{ tag }}</h3>
  {% capture posts %}{% for post in site.tags[tag] %}{% unless forloop.first %}|{% endunless %}{{ post.title }}#{{ post.url }}{% endfor %}{% endcapture %}
  {% assign sortedposts = posts | split: '|' | sort %}
  <ul>
  {% for post in sortedposts %}{% assign postitems = post | split: '#' %}
    <li><a href="{{ site.github.url }}{{ postitems[1] }}">{{ postitems[0] }}</a></li>
  {% endfor %}
  </ul>
</div>
{% endfor %}





