---
layout: archive
title: "Publications"
permalink: /publications/
author_profile: true
---

Note: This page might be out of date. For a more updated list of publications, visit <a href="https://scholar.google.com/citations?user=fNxrh48AAAAJ&hl=en&authuser=1">my Google Scholar profile</a>. 

{% include base_path %}

<div style="max-width: 100%; margin: 20px 0;">
  <input type="text" id="pubSearch" onkeyup="filterPubs()" placeholder=" Search by title, keyword, or year..." 
         style="width: 100%; padding: 12px; border: 1px solid #ddd; border-radius: 4px; font-size: 1rem; box-sizing: border-box;">
  
  <div id="noResults" style="display:none; color: #cc0000; font-weight: bold; margin-top: 15px;">
    No matching publications found.
  </div>
</div>

<div id="pubList">
  {% for post in site.publications reversed %}
    <div class="pub-item">
      {% include archive-single.html %}
    </div>
  {% endfor %}
</div>

<script>
function filterPubs() {
  var input = document.getElementById('pubSearch');
  var filter = input.value.toLowerCase();
  var items = document.getElementsByClassName('pub-item');
  var noResults = document.getElementById('noResults');
  var visibleCount = 0;

  for (var i = 0; i < items.length; i++) {
    // Searches through all text inside the publication item
    if (items[i].innerText.toLowerCase().includes(filter)) {
      items[i].style.display = "block";
      visibleCount++;
    } else {
      items[i].style.display = "none";
    }
  }
  noResults.style.display = (visibleCount === 0 && filter !== "") ? "block" : "none";
}
</script>
