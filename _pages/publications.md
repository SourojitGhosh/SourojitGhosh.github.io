---
layout: archive
title: "Publications"
permalink: /publications/
author_profile: true
---

Note: This page might be out of date. For a more updated list of publications, visit <a href="https://scholar.google.com/citations?user=fNxrh48AAAAJ&hl=en&authuser=1">my Google Scholar profile</a>. 

{% include base_path %}

{% for post in site.publications reversed %}
  {% include archive-single.html %}
{% endfor %}
