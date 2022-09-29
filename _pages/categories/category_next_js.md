---
title: "Next.js"
layout: archive
permalink: /categories/next_js
author_profile: true
sidebar:
  nav: "sidebar"
---

<h2> {{ site.categories["Next.js"] | size }} 개의 포스트 </h2>

{% assign posts = site.categories["Next.js"] %}

{% for post in posts %}
{% include archive-single.html type=page.entries_layout %}
{% endfor %}
