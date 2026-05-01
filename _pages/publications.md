---
layout: archive
title: "Publications"
permalink: /publications/
author_profile: true
---

Note: This page might be out of date. For a more updated list of publications, visit <a href="https://scholar.google.com/citations?user=fNxrh48AAAAJ&hl=en&authuser=1">my Google Scholar profile</a>. 

{% include base_path %}

<div style="display: flex; gap: 10px; margin: 20px 0; max-width: 100%; flex-wrap: wrap;">
  <input type="text" id="pubSearch" placeholder="Search title, year, or venue (e.g. CSCW, AIES)..." 
         style="flex-grow: 2; min-width: 250px; padding: 12px; border: 2px solid #444 !important; border-radius: 4px; font-size: 1rem; background-color: #ffffff !important; color: #000000 !important; display: block !important;">
  
  <button onclick="filterPubs()" 
          style="flex-grow: 0.5; padding: 10px 20px; background-color: #007fae; color: #ffffff !important; border: none; border-radius: 4px; cursor: pointer; font-weight: bold;">
    Search
  </button>

  <button onclick="clearSearch()" 
          style="flex-grow: 0.1; padding: 10px 15px; background-color: #eeeeee; color: #333333 !important; border: 1px solid #cccccc; border-radius: 4px; cursor: pointer;">
    Clear
  </button>
</div>

<div id="noResults" style="display:none; color: #cc0000; font-weight: bold; margin-bottom: 20px;">
  No matching publications found.
</div>

<div id="pubList">
  {% for post in site.publications reversed %}
    <div class="pub-wrapper" data-venue="{{ post.venue | downcase }}">
      {% include archive-single.html %}
    </div>
  {% endfor %}
</div>

<script>
function filterPubs() {
  const input = document.getElementById('pubSearch');
  const filter = input.value.toLowerCase().trim();
  
  // Select our wrappers
  const items = document.querySelectorAll('.pub-wrapper');
  const noResults = document.getElementById('noResults');
  let visibleCount = 0;

  items.forEach(item => {
    // Get all text content and the specific venue data attribute
    const text = (item.textContent || "").toLowerCase();
    const venue = (item.getAttribute('data-venue') || "").toLowerCase();
    
    // Check if search term matches title/body OR the venue metadata
    if (text.includes(filter) || venue.includes(filter)) {
      item.style.setProperty('display', 'block', 'important');
      visibleCount++;
    } else {
      item.style.setProperty('display', 'none', 'important');
    }
  });

  // Handle No Results message
  if (visibleCount === 0 && filter !== "") {
    noResults.style.setProperty('display', 'block', 'important');
  } else {
    noResults.style.setProperty('display', 'none', 'important');
  }
}

function clearSearch() {
  document.getElementById('pubSearch').value = "";
  filterPubs();
}

// Ensure Enter key triggers search
document.getElementById('pubSearch').addEventListener("keydown", function(e) {
  if (e.key === "Enter") {
    e.preventDefault();
    filterPubs();
  }
});
</script>
