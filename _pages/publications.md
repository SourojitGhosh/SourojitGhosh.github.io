---
layout: archive
title: "Publications"
permalink: /publications/
author_profile: true
---

Note: This page might be out of date. For a more updated list of publications, visit <a href="https://scholar.google.com/citations?user=fNxrh48AAAAJ&hl=en&authuser=1">my Google Scholar profile</a>. 

{% include base_path %}

<div style="display: flex; gap: 10px; margin: 20px 0; max-width: 100%;">
  <input type="text" id="pubSearch" placeholder="Search by title, keyword, venue, or year..." 
         style="flex-grow: 1; padding: 12px; border: 1px solid #ddd; border-radius: 4px; font-size: 1rem;">
  
  <button onclick="filterPubs()" 
          style="padding: 10px 20px; background-color: #007fae; color: white; border: none; border-radius: 4px; cursor: pointer; font-weight: bold;">
    Search
  </button>
</div>

<div id="noResults" style="display:none; color: #cc0000; font-weight: bold; margin-bottom: 20px;">
  No matching publications found.
</div>

<div id="pubList">
  {% for post in site.publications reversed %}
    {% include archive-single.html %}
  {% endfor %}
</div>

<script>
function filterPubs() {
  var input = document.getElementById('pubSearch');
  var filter = input.value.toLowerCase().trim();
  
  var items = document.querySelectorAll('.archive__item');
  var noResults = document.getElementById('noResults');
  var visibleCount = 0;

  for (var i = 0; i < items.length; i++) {
    // textContent grabs the text regardless of the extension's spans
    var text = items[i].textContent || items[i].innerText;
    
    if (text.toLowerCase().indexOf(filter) > -1) {
      items[i].style.display = "block";
      visibleCount++;
    } else {
      items[i].style.display = "none";
    }
  }

  noResults.style.display = (visibleCount === 0 && filter !== "") ? "block" : "none";
}

document.getElementById('pubSearch').addEventListener("keypress", function(event) {
  if (event.key === "Enter") {
    event.preventDefault();
    filterPubs();
  }
});
</script>
