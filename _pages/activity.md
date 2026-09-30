---
title: "Activity"
permalink: /activity/
---

연구 · 강의 · 특강 활동 기록입니다. 최신순으로 정리했습니다.

{% assign current_year = "" %}
<div class="news-list">
{%- for n in site.data.news %}
{%- assign y = n.date | slice: 0, 4 %}
{%- if y != current_year %}
{%- unless current_year == "" %}</ul>{% endunless %}
<h2 class="news-year">{{ y }}</h2>
<ul>
{%- assign current_year = y %}
{%- endif %}
<li><span class="news-date">{{ n.date }}</span> {% if n.link %}<a href="{{ n.link }}">{{ n.text }}</a>{% else %}{{ n.text }}{% endif %}</li>
{%- endfor %}
</ul>
</div>
