---
layout: archive
title: "Research and Publications"
permalink: /publications/
author_profile: true
---
My research interests lie mainly in symplectic geometry and more specifically, I apply various Floer homology theories to problems concerning the interplay of symplectic geometry with other fields such as algebraic singularities. I also have interest in almost complex geometry and have an undergraduate paper in algebraic topology and one on the generalized eigenvalue problem.

{% if author.googlescholar %}
  You can also find my articles on <u><a href="{{author.googlescholar}}">my Google Scholar profile</a>.</u>
{% endif %}

{% include base_path %}

{% for post in site.publications reversed %}
  {% include archive-single.html %}
{% endfor %}
