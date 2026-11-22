---
layout: default
title: About
permalink: /
---
{% assign p = site.data.profile %}
<section class="hero">
  <img class="portrait" src="{{ site.author.photo | relative_url }}" alt="{{ site.author.name }}">
  <div class="hero-text">
    <h1>{{ site.author.name }}</h1>
    <p class="role">{{ site.author.role }}<br>{{ site.author.institution }}</p>
    {% include links.html %}
  </div>
</section>

<section class="about prose">
  {% if p.figure %}
  <figure class="landscape">
    {% include landscape-figure.html %}
    {% if p.figure.caption %}<figcaption>{{ p.figure.caption }}</figcaption>{% endif %}
  </figure>
  {% endif %}
  {{ p.bio | markdownify }}
  {{ p.bio_more | markdownify }}
</section>

{% if p.interests %}
<section>
  <h2>Research interests <span class="hint">click a topic to see related publications</span></h2>
  <ul class="pills">{% for i in p.interests %}<li><a href="{{ '/publications/' | relative_url }}?tag={{ i | url_encode }}" title="Publications on {{ i }}">{{ i }}</a></li>{% endfor %}</ul>
</section>
{% endif %}

<div class="two-col">
  <section>
    <h2>Positions</h2>
    <ul class="timeline">
      {% for e in p.positions %}
      <li><span class="when">{{ e.period }}</span><span class="what"><strong>{{ e.title }}</strong>{% if e.unit %}<br>{{ e.unit }}{% endif %}<br>{{ e.institution }}{% if e.note %}<br><small>{{ e.note }}</small>{% endif %}</span></li>
      {% endfor %}
    </ul>
  </section>
  <section>
    <h2>Education</h2>
    <ul class="timeline">
      {% for e in p.education %}
      <li><span class="when">{{ e.period }}</span><span class="what"><strong>{{ e.title }}</strong>{% if e.unit %}<br>{{ e.unit }}{% endif %}<br>{{ e.institution }}{% if e.note %}<br><small>{{ e.note }}</small>{% endif %}</span></li>
      {% endfor %}
    </ul>
  </section>
</div>

{% assign selected = site.data.publications | where: "selected", true %}
{% if selected.size > 0 %}
<section>
  <h2>Selected publications <a class="more" href="{{ '/publications/' | relative_url }}">All publications →</a></h2>
  <ul class="pub-list">
    {% for pub in selected %}{% include publication.html pub=pub %}{% endfor %}
  </ul>
</section>
{% endif %}

{% assign works = site.designs | sort: "order" %}
{% if works.size > 0 %}
<section>
  <h2>Design works <a class="more" href="{{ '/designs/' | relative_url }}">All design works →</a></h2>
  <div class="cards">
    {% for work in works limit: 4 %}{% include design-card.html work=work %}{% endfor %}
  </div>
</section>
{% endif %}

{% if p.awards %}
<section>
  <h2>Awards</h2>
  <ul class="timeline">
    {% for a in p.awards %}
    <li><span class="when">{{ a.year }}</span><span class="what"><strong>{{ a.title }}</strong><br>{% if a.url %}<a href="{{ a.url }}" target="_blank" rel="noopener">{{ a.detail }}</a>{% else %}{{ a.detail }}{% endif %}</span></li>
    {% endfor %}
  </ul>
</section>
{% endif %}
