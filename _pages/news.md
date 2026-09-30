---
title: "News"
permalink: /news/
redirect_from:
  - /activity/
---

연구 · 강의 · 특강 활동 기록입니다. 최신순으로 정리했습니다.
<span lang="en">Research, teaching, and outreach activities, newest first.</span>

{% assign current_year = "" %}
<div class="news-archive">
{%- for n in site.data.news %}
{%- assign y = n.date | slice: 0, 4 %}
{%- if y != current_year %}
{%- unless current_year == "" %}</ul>{% endunless %}
<h2 class="news-year">{{ y }}</h2>
<ul class="news-list">
{%- assign current_year = y %}
{%- endif %}
{% include news-item.html n=n %}
{%- endfor %}
</ul>
</div>
