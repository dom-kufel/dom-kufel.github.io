---
layout: page
title: Publications
description: >
  Publications by Dominik Kufel on AI for quantum many-body physics, neural quantum states, and quantum computing.
hide_description: true
permalink: /publications/
---

{%- assign pubs = site.data.publications -%}
{%- assign n_ai = pubs.selected | where_exp: "p", "p.topics contains 'ai'" | size -%}
{%- assign n_qc = pubs.selected | where_exp: "p", "p.topics contains 'qc'" | size -%}
{%- assign n_sensing = pubs.selected | where_exp: "p", "p.topics contains 'sensing'" | size -%}
{%- assign n_all = pubs.selected.size | plus: pubs.earlier.size -%}

<div class="pubs">
<input class="pubs__radio" type="radio" name="pubs-filter" id="pf-all" checked>
<input class="pubs__radio" type="radio" name="pubs-filter" id="pf-ai">
<input class="pubs__radio" type="radio" name="pubs-filter" id="pf-qc">
<input class="pubs__radio" type="radio" name="pubs-filter" id="pf-sensing">
<input class="pubs__radio" type="radio" name="pubs-filter" id="pf-earlier">
<div class="pubs__filters" role="group" aria-label="Filter publications">
<label for="pf-all">All <span>{{ n_all }}</span></label>
<label for="pf-ai">AI &amp; Condensed Matter <span>{{ n_ai }}</span></label>
<label for="pf-qc">Quantum Computing <span>{{ n_qc }}</span></label>
<label for="pf-sensing">Quantum Sensing <span>{{ n_sensing }}</span></label>
<label for="pf-earlier">Earlier work <span>{{ pubs.earlier.size }}</span></label>
</div>
<section class="pubs__section pubs__selected">
<h2 class="section-label">Selected</h2>
<div class="pubs__list">
{%- for p in pubs.selected %}{% include pub-card.html pub=p %}{% endfor %}
</div>
<p class="pubs__note">* equal contribution</p>
</section>
<section class="pubs__section pubs__earlier">
<h2 class="section-label">Earlier work</h2>
<div class="pubs__list pubs__list--compact">
{%- for p in pubs.earlier %}{% include pub-card.html pub=p %}{% endfor %}
</div>
</section>
<section class="pubs__section pubs__refereeing">
<h2 class="section-label">Refereeing</h2>
<ul class="pubs__chips">
{%- for r in pubs.refereeing %}<li>{{ r }}</li>{% endfor %}
</ul>
</section>
</div>
