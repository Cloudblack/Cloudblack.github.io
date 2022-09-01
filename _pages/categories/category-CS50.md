---
title: "CS50"
layout: category
permalink: categories/CS50
author_profile: true
sidebar_main: true
---

{% assign posts = site.categories.CS50 %}
{% for post in posts %} {% include archive-single2.html type=page.entries_layout %} {% endfor %}