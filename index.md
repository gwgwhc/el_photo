---
title: home
layout: home
type: parent
order: 1
---

<div class="section header">
	<div class="container">
		<h3 class="section-heading">@analogwgwhc</h3>
		<div id="navbar-wrapper">
			<div id="navbar">
				{% assign mypages = site.pages | where: "type", "parent" | sort: "order" %}
				{% for page in mypages %}
				<a class="button" href="{{ page.url | relative_url }}">{{ page.title }}</a>
				{% endfor %}
			</div>
		</div>
	</div>
</div>

<div class="section main">
	<div class="container">
		<div class="row" id="gallery">
			{% assign coll = site.collections | where: "label", "images" | first %}
			{% assign list = coll.files | sort: "basename" %}
			{% assign l = coll.files.size | divided_by: 2 | ceil %}
			<div class="one-half column">
				{% for image in coll.files limit: l %}
				<article class="thumb">
					<img class="lozad u-max-full-width" data-src="{{ coll.label | append: '/' | append: image.name | relative_url }}" alt="{{ image.basename }}" />
				</article>
				{% endfor %}
			</div>
			<div class="one-half column">
				{% for image in coll.files offset: l %}
				<article class="thumb">
					<img class="lozad u-max-full-width" data-src="{{ coll.label | append: '/' | append: image.name | relative_url }}" alt="{{ image.basename }}" />
				</article>
				{% endfor %}
			</div>
		</div>
	</div>
</div>