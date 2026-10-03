---
layout: page
title: Outreach
description: >
permalink: /outreach/
---

<figure class="outreach-hero">
  <img src="/assets/img/outreach/american_centre.jpg" alt="Outreach activities">
  <figcaption>Highlight from an outreach activity (photo courtesy of American Corner in Lublin)</figcaption>
</figure>

<section class="pubs__section">
<h2 class="section-label">Talks, workshops &amp; writing</h2>
<div class="outreach-grid">
{%- for o in site.data.outreach %}
<a class="outreach-card" href="{{ o.url | relative_url }}">
  {%- if o.image %}
  <span class="outreach-card__image"><img src="{{ o.image | relative_url }}" alt="" loading="lazy" decoding="async"></span>
  {%- else %}
  <span class="outreach-card__image outreach-card__image--text"><span>{{ o.icon_text }}</span></span>
  {%- endif %}
  <span class="outreach-card__body">
    <span class="talk-card__tags"><span class="talk-pill">{{ o.kind }}</span><span class="talk-pill talk-pill--audience">{{ o.audience }}</span></span>
    <span class="outreach-card__title heading">{{ o.title }}</span>
    <span class="outreach-card__summary">{{ o.summary }}</span>
    <span class="outreach-card__meta">{{ o.date }} · {{ o.location }}</span>
  </span>
</a>
{%- endfor %}
</div>
</section>
