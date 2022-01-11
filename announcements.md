---
layout: default
title: Announcements
nav_exclude: true
description: A feed containing all of the class announcements.
---

# Announcements

Please also check Canvas for class announcements.

{% assign announcements = site.announcements | reverse %}
{% for announcement in announcements %}
{{ announcement }}
{% endfor %}
