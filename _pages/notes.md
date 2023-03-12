---
layout: default
title: Notes and Materials
nav_title: Notes
permalink: /notes/
description: Compilation of notes and useful materials.
nav: true
nav_order: 3
display_categories: [Maths]
horizontal: false
---

<div class="post">

  <div class="header-bar">
    <h1>{{ site.blog_name }}</h1>
    <h2> A collection of technical notes and materials. </h2>
  </div>
</div>

<div class="projects">
{%- if site.enable_note_categories and page.display_categories %}
  <!-- Display categorized projects -->
  {%- for category in page.display_categories %}
  <h2 class="category">{{ category }}</h2>
  {%- assign categorized_notes = site.notes | where: "category", category -%}
  {%- assign sorted_notes = categorized_notes | sort: "date" | reverse %}
  <!-- Generate lines for each project -->
  <ul class="post-list">
    {% for post in sorted_notes %}
    {% assign read_time = post.feed_content | strip_html | number_of_words | divided_by: 180 | plus: 1 %}
    {% assign year = post.date | date: "%Y" %}
    <li>
      <h3>
        {% if post.redirect == blank %}
          <a class="post-title" href="{{ post.url | prepend: site.baseurl }}">{{ post.title }}</a>
        {% else %}
          {% if post.redirect contains '://' %}
            <a class="post-title" href="{{ post.redirect }}" target="_blank">{{ post.title }}</a>
            <svg width="2rem" height="2rem" viewBox="0 0 40 40" xmlns="http://www.w3.org/2000/svg">
              <path d="M17 13.5v6H5v-12h6m3-3h6v6m0-6-9 9" class="icon_svg-stroke" stroke="#999" stroke-width="1.5" fill="none" fill-rule="evenodd" stroke-linecap="round" stroke-linejoin="round"></path>
            </svg>
          {% else %}
            <a class="post-title" href="{{ post.redirect | relative_url }}">{{ post.title }}</a>
          {% endif %}
        {% endif %}
      </h3>
      <p>{{ post.description }}</p>
      <p class="post-meta">
        {{ read_time }} min read &nbsp; &middot; &nbsp;
        {{ post.date | date: '%B %-d, %Y' }}
        {%- if post.external_source %}
        &nbsp; &middot; &nbsp; {{ post.external_source }}
        {%- endif %}
      </p>
    </li>
    {% endfor %}
  </ul>
  {% endfor %}

{%- else -%}
<!-- Display projects without categories -->
  {%- assign sorted_notes = site.notes | sort: "date" | reverse -%}
  <!-- Generate cards for each project -->
  <ul class="post-list">
    {% for post in sorted_notes %}
    {% assign read_time = post.feed_content | strip_html | number_of_words | divided_by: 180 | plus: 1 %}
    {% assign year = post.date | date: "%Y" %}
    <li>
      <h3>
        {% if post.redirect == blank %}
          <a class="post-title" href="{{ post.url | prepend: site.baseurl }}">{{ post.title }}</a>
        {% else %}
          {% if post.redirect contains '://' %}
            <a class="post-title" href="{{ post.redirect }}" target="_blank">{{ post.title }}</a>
            <svg width="2rem" height="2rem" viewBox="0 0 40 40" xmlns="http://www.w3.org/2000/svg">
              <path d="M17 13.5v6H5v-12h6m3-3h6v6m0-6-9 9" class="icon_svg-stroke" stroke="#999" stroke-width="1.5" fill="none" fill-rule="evenodd" stroke-linecap="round" stroke-linejoin="round"></path>
            </svg>
          {% else %}
            <a class="post-title" href="{{ post.redirect | relative_url }}">{{ post.title }}</a>
          {% endif %}
        {% endif %}
      </h3>
      <p>{{ post.description }}</p>
      <p class="post-meta">
        {{ read_time }} min read &nbsp; &middot; &nbsp;
        {{ post.date | date: '%B %-d, %Y' }}
        {%- if post.external_source %}
        &nbsp; &middot; &nbsp; {{ post.external_source }}
        {%- endif %}
      </p>
    </li>
    {% endfor %}
  </ul>
{% endif %}
</div>
