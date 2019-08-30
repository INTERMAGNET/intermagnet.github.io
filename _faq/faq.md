---
title: "INTERMAGNET FAQ"
permalink: /faq/index.html
---
{% for item in site.faq %}
{% if item.title != "INTERMAGNET FAQ" %}
- [{{ item.title }}]({{ item.url }})
{% endif %}
{% endfor %}