---
layout: default
title: Home
---

# Welcome to My Website

Hello! I’m John Vusich, a Cell and Molecular Biology PhD student
  studying computational and cancer biology in the Andrechek lab at MSU. 
  This showcases my projects, publications, and more. 
  Explore the links below to learn more about me.

- [About Me](about.html)
- [Projects](projects.html)
- [Publications](publications.html)
- [Contact](contact.html)

## Latest Blog Posts

{% for post in site.posts %}
- [{{ post.title }}]({{ post.url }})
{% endfor %}
