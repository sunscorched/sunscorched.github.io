---
layout: archive
title: "Research and Publications"
permalink: /publications/
author_profile: true
---
My current interests are in machine learning and quantitative finance. I completed a project in Fall 2024 on [the effects of Daylight Savings Time on market outcomes](https://www.erdosinstitute.org/project-database/fall-2024/data-science-boot-camp/the-effects-of-daylight-savings-on-market-outcomes) and am currently working on [predicting the price of agriculture future contracts with exogenous factors](https://tianhaow.github.io/ErdosAgriDerivPredict/). I also have some work in progress on developing [binomial trees with nonconstant volatility for options pricing](https://github.com/sunscorched/OptionsPricing). In the Large Language Model sphere, I have contributed prompt engineering and benchmark data specifically for LLMs tasked with solving complex math problems. 

Formerly, my research interests were mainly in symplectic geometry and more specifically, I applied various Floer homology theories to problems concerning the interplay of symplectic geometry with other fields such as algebraic singularities. I also studied almost complex geometry and have an undergraduate paper in algebraic topology and one on the generalized eigenvalue problem.

{% if author.googlescholar %}
  You can also find my articles on <u><a href="{{author.googlescholar}}">my Google Scholar profile</a>.</u>
{% endif %}

{% include base_path %}

{% for post in site.publications reversed %}
  {% include archive-single.html %}
{% endfor %}
