---
title: Home
layout: home
type: home
order: 1
---

<div class="section">
	<div class="container">
		<img src="{{ "/assets/images/logo.png" | relative_url }}">
		<h3 class="section-heading">Photoraphy</h3>
		<p class="section-description">
			Discovering the world with my vision.
		</p>
		{% assign mypages = site.pages | where: "type", "home" | sort: "order" %}
		{% for page in mypages %}
		<a class="button" href="{{ page.url | relative_url }}">{{ page.title }}</a>
		{% endfor %}
	</div>
</div>
<div class="section">
	<div class="container">
		<div class="row">
			<div class="one-half column">
				{% assign coll = site.collections | where: "label", "home" | first %}
				{% assign l = coll.files.size | divided_by: 2 | floor %}
				{% for image in coll.files limit: l %}
				<img class="u-max-full-width" src="{{ coll.label | append: '/' | append: image.name }}" alt="{{ image.basename }}" />
				{% endfor %}
			</div>
			<div class="one-half column">
				{% for image in coll.files offset: l %}
				<img class="u-max-full-width" src="{{ coll.label | append: '/' | append: image.name }}" alt="{{ image.basename }}" />
				{% endfor %}
			</div>
		</div>
	</div>
</div>