---
layout: "single"
permalink: "/gallery/"
title: "Media & Documents"
sidebar:
  nav: main
classes: "wide"
---
Add photos, videos, and documents by editing the YAML data file at `_data/manifest.yml`. Files go under `/assets/images/`, `/assets/media/`, or `/content/`.

{% assign media = site.data.manifest.media %}
{% assign documents = site.data.manifest.documents %}

{% if media %}
## Media
<div class="grid__wrapper">
{% for item in media %}
  <div class="archive__item">
    <div class="archive__item-teaser">
      {% if item.type == 'image' %}
        <img src="{{ item.src }}" alt="{{ item.title }}">
      {% elsif item.type == 'video' %}
        <video src="{{ item.src }}" controls></video>
      {% elsif item.type == 'embed' %}
        <iframe src="{{ item.src }}" style="width:100%;height:280px;border:1px solid #e5e7eb;border-radius:12px;"></iframe>
      {% endif %}
    </div>
    <h2 class="archive__item-title">{{ item.title }}</h2>
    {% if item.description %}<p class="archive__item-excerpt">{{ item.description }}</p>{% endif %}
    <p class="page__meta">{{ item.date }}{% if item.tags %} • {{ item.tags | join: ', ' }}{% endif %}</p>
    <p><a class="btn" href="{{ item.src }}" target="_blank">Open</a></p>
  </div>
{% endfor %}
</div>
{% endif %}

{% if documents %}
## Documents & Links
<ul>
{% for doc in documents %}
  <li>
    <strong>{{ doc.title }}</strong> — {{ doc.description }}
    <br><small>{{ doc.type }} • {{ doc.date }}</small>
    <br><a href="{{ doc.src }}" target="_blank">Open</a>
    {% if doc.tags %}<br><small>Tags: {{ doc.tags | join: ', ' }}</small>{% endif %}
  </li>
{% endfor %}
</ul>
{% endif %}
