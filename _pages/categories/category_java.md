---
title: "Java"
layout: archive
permalink: /categories/java
author_profile: true
sidebar:
  nav: "sidebar"
---

<h2> {{ site.categories["Java"] | size }} 개의 포스트 </h2>
-----
{% assign posts = site.categories["Java"] %}


{% for post in posts %}
  {% include archive-single.html type=page.entries_layout %}
{% endfor %}
