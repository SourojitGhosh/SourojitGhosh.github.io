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

  window.clearSearch = function() {
    const input = document.getElementById('pubSearch');
    if (input) {
      input.value = "";
      window.filterPubs();
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

<div style="display: flex; gap: 8px; margin: 20px 0; max-width: 100%; align-items: center !important;">
  
  <input type="text" id="pubSearch" placeholder="Search title, year, or venue..." 
         style="flex-grow: 1; min-width: 0; height: 42px !important; padding: 0 12px !important; border: 2px solid #000000 !important; border-radius: 4px !important; font-size: 16px !important; background-color: #ffffff !important; color: #000000 !important; box-sizing: border-box !important; margin: 0 !important; vertical-align: middle !important;">
  
  <button onclick="window.filterPubs()" 
          style="height: 42px !important; padding: 0 20px !important; background-color: #007fae !important; color: #ffffff !important; border: none !important; border-radius: 4px !important; cursor: pointer !important; font-weight: bold !important; white-space: nowrap !important; box-sizing: border-box !important; margin: 0 !important; vertical-align: middle !important; display: inline-flex; align-items: center; justify-content: center; line-height: 1 !important;">
    Search
  </button>

  <button onclick="window.clearSearch()" 
          style="height: 42px !important; padding: 0 15px !important; background-color: #e0e0e0 !important; color: #333333 !important; border: 1px solid #cccccc !important; border-radius: 4px !important; cursor: pointer   !important; white-space: nowrap !important; box-sizing: border-box !important; margin: 0 !important; vertical-align: middle !important; display: inline-flex; align-items: center; justify-content: center; line-height: 1 !important;">
    Clear
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
