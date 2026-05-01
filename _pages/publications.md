---
layout: archive
title: "Publications"
permalink: /publications/
author_profile: true
---

<script>
  window.filterPubs = function() {
    const input = document.getElementById('pubSearch');
    if (!input) return;
    const filter = input.value.toLowerCase().trim();
    
    const items = document.querySelectorAll('.archive__item');
    const noResults = document.getElementById('noResults');
    let visibleCount = 0;

    for (let i = 0; i < items.length; i++) {
      const item = items[i];
      const text = (item.textContent || item.innerText).toLowerCase();
      
      if (text.includes(filter)) {
        item.style.setProperty('display', 'block', 'important');
        visibleCount++;
      } else {
        item.style.setProperty('display', 'none', 'important');
      }
    }

    if (noResults) {
      noResults.style.setProperty('display', (visibleCount === 0 && filter !== "") ? 'block' : 'none', 'important');
    }
  };

  document.addEventListener('keydown', function(e) {
    if (e.target && e.target.id === 'pubSearch' && e.key === 'Enter') {
      e.preventDefault();
      window.filterPubs();
    }
  });
</script>

Note: This page might be out of date. For a more updated list of publications, visit <a href="https://scholar.google.com/citations?user=fNxrh48AAAAJ&hl=en&authuser=1">my Google Scholar profile</a>. 

{% include base_path %}

<div style="display: flex; gap: 10px; margin: 20px 0; max-width: 100%;">
  <input type="text" id="pubSearch" placeholder="Search title, year, or venue..." 
         style="flex-grow: 1; padding: 10px; border: 2px solid #444 !important; border-radius: 4px; font-size: 1rem; background-color: #fff !important; color: #00 !important;">
  
  <button onclick="window.filterPubs()" 
          style="padding: 10px 20px; background-color: #007fae; color: #fff !important; border: none; border-radius: 4px; cursor: pointer; font-weight: bold;">
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
