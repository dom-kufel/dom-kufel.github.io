---
layout: page
title: Recent Talks & Posters
description: >
  Recent talks, seminars, and posters.
permalink: /talks/
---

{%- assign upcoming = site.data.talks | where: "upcoming", true -%}
{%- assign recurring = site.data.talks | where: "recurring", true -%}
{%- assign past = site.data.talks | where_exp: "t", "t.upcoming != true" | where_exp: "t", "t.recurring != true" | group_by: "year" -%}

<div class="talks">
{%- if upcoming.size > 0 %}
<section class="talks__section">
<h2 class="section-label">Upcoming</h2>
<div class="talks__list">
{%- for t in upcoming %}{% include talk-card.html talk=t %}{% endfor %}
</div>
</section>
{%- endif %}
{%- for group in past %}
<section class="talks__section">
<h2 class="section-label">{{ group.name }}</h2>
<div class="talks__list">
{%- for t in group.items %}{% include talk-card.html talk=t %}{% endfor %}
</div>
</section>
{%- endfor %}
{%- if recurring.size > 0 %}
<section class="talks__section">
<h2 class="section-label">Recurring</h2>
<div class="talks__list">
{%- for t in recurring %}{% include talk-card.html talk=t %}{% endfor %}
</div>
</section>
{%- endif %}
</div>
