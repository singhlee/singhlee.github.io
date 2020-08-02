---
layout: page
title: About
description: 
keywords: SinghLee
comments: true
menu: 关于
permalink: /about/
---

不断前行，不断改变

## 联系

<ul>
{% for website in site.data.social %}
<li>{{website.sitename }}：<a href="{{ website.url }}" target="_blank">@{{ website.name }}</a></li>
{% endfor %}
<!-- {% if site.url contains 'mazhuang.org' %}

{% endif %} -->
</ul>


## Skill Keywords

{% for skill in site.data.skills %}
### {{ skill.name }}
<div class="btn-inline">
{% for keyword in skill.keywords %}
<button class="btn btn-outline" type="button">{{ keyword }}</button>
{% endfor %}
</div>
{% endfor %}