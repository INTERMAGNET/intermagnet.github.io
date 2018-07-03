---
title: "INTERMAGNET FAQs"
---

<ol>
{% for item in site.faq %}
    <li>
        <a href="{{ item.url }}">
            {{ item.title }}
        </a>
    </li>
{% endfor %}
</ol>
