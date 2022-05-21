---
title: "Error"
layout: archive
permalink: /categories/error
author_profile: true
sidebar:
  nav: "sidebar"
---

<h2> {{ site.categories["Error"] | size }} 개의 포스트 </h2>
-----
{% assign posts = site.categories["Error"] %}


{% for post in posts %}
  {% include archive-single.html type=page.entries_layout %}
{% endfor %}
