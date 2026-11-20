---
layout: default
title: Publications
permalink: /publications/
description: Journal and conference publications by Qihao Zhu.
---
{% assign pubs = site.data.publications %}
{% assign journal = pubs | where: "type", "journal" %}
{% assign conference = pubs | where: "type", "conference" %}
{% comment %} Tag list: research interests first (in their order), then any other tag used by a paper. {% endcomment %}
{% assign all_tags = site.data.profile.interests %}
{% for pub in pubs %}{% for t in pub.tags %}{% unless all_tags contains t %}{% assign all_tags = all_tags | push: t %}{% endunless %}{% endfor %}{% endfor %}

<h1>Publications</h1>
<p class="muted">{{ journal.size }} journal papers · {{ conference.size }} peer-reviewed conference papers{% if site.author.scholar != "" %} · <a href="{{ site.author.scholar }}" target="_blank" rel="noopener">Google Scholar</a>{% endif %}</p>

<div class="filter" id="filter">
  <span class="filter-label">Filter by topic:</span>
  <a href="{{ '/publications/' | relative_url }}" class="chip active" data-tag="">All</a>
  {% for t in all_tags %}<a href="{{ '/publications/' | relative_url }}?tag={{ t | url_encode }}" class="chip" data-tag="{{ t }}">{{ t }}</a>{% endfor %}
</div>
<p class="filter-status muted" id="filter-status" hidden></p>

{% if journal.size > 0 %}
<section class="pub-group">
<h2 id="journal">Journal papers</h2>
<ul class="pub-list">{% for pub in journal %}{% include publication.html pub=pub %}{% endfor %}</ul>
</section>
{% endif %}

{% if conference.size > 0 %}
<section class="pub-group">
<h2 id="conference">Peer-reviewed conference papers</h2>
<ul class="pub-list">{% for pub in conference %}{% include publication.html pub=pub %}{% endfor %}</ul>
</section>
{% endif %}

<script>
(function () {
  var chips = document.querySelectorAll('#filter .chip');
  var pubs = document.querySelectorAll('.pub');
  var groups = document.querySelectorAll('.pub-group');
  var status = document.getElementById('filter-status');

  function apply(tag, push) {
    var n = 0;
    pubs.forEach(function (li) {
      var tags = (li.getAttribute('data-tags') || '').split('|');
      var show = !tag || tags.indexOf(tag) !== -1;
      li.hidden = !show; if (show) n++;
    });
    groups.forEach(function (g) {
      g.hidden = !g.querySelector('.pub:not([hidden])');
    });
    chips.forEach(function (c) { c.classList.toggle('active', (c.getAttribute('data-tag') || '') === (tag || '')); });
    status.hidden = !tag;
    if (tag) status.textContent = n + (n === 1 ? ' publication tagged “' : ' publications tagged “') + tag + '”';
    if (push) {
      var url = location.pathname + (tag ? '?tag=' + encodeURIComponent(tag) : '');
      history.replaceState(null, '', url);
    }
  }
  chips.forEach(function (c) {
    c.addEventListener('click', function (e) { e.preventDefault(); apply(c.getAttribute('data-tag'), true); });
  });
  document.querySelectorAll('.pub-tags a').forEach(function (a) {
    a.addEventListener('click', function (e) { e.preventDefault(); apply(a.getAttribute('data-tag'), true); window.scrollTo({ top: 0, behavior: 'smooth' }); });
  });
  var initial = new URLSearchParams(location.search).get('tag');
  if (initial) apply(initial, false);
})();
</script>
