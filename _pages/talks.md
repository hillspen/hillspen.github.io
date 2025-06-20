---
layout: page
title: talks
permalink: /talks/
description: Slides and other material for the talks I have given.
nav: true
nav_order: 7
---

Slides and other material for the talks I have given.

{% assign talks = site.data.talks | sort: 'date' | reverse %}
{% assign last_year = '' %}

<ul>
{% for talk in talks %}
  {% assign year = talk.date | slice: 0, 4 %}
  {% if year != last_year %}
    {% unless forloop.first %}</ul>{% endunless %}
    <h2>{{ year }}</h2>
    <ul>
    {% assign last_year = year %}
  {% endif %}
  <li style="margin-bottom: 1.5em;">
    <b>{{ talk.date | date: '%d %b' }}:</b>
    {% if talk.link %}
      <a href="{{ talk.link }}" target="_blank">{{ talk.title }}</a>
    {% else %}
      {{ talk.title }}
    {% endif %}
    <span class="text-muted"> — {{ talk.location }}</span>
  </li>
{% endfor %}
</ul>
