---
layout: default
title: Design Works
permalink: /designs/
description: Industrial design and prototyping projects by Qihao Zhu.
---
<h1>Design Works</h1>
<p class="muted">Selected industrial design and prototyping projects.</p>

{% assign works = site.designs | sort: "order" %}
<div class="cards">
  {% for work in works %}{% include design-card.html work=work %}{% endfor %}
</div>
