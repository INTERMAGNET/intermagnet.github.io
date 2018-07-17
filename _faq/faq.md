---
title: "INTERMAGNET FAQs"
permalink: /faq/index.html
---
{% for item in site.faq %}

- [{{ item.title }}]({{ item.url }})

{% endfor %}
