---
layout: page
title: Home
id: home
permalink: /
---

{% assign recent_notes = site.notes | sort: "last_modified_at_timestamp" | reverse %}
{% for note in recent_notes limit: 1 %}

{% capture words %}
{{ note.content | number_of_words }}
{% endcapture %}

<a class="internal-link" href="{{ site.baseurl }}{{ note.url }}">Latest</a>

## {{note.title}}

  <p class="faint small">{{ note.last_modified_at | date: "%-d %B, %Y" }} • {{ words | divided_by: 180 | append: ' minute read' }}</p>
  <p>{{note.excerpt}} <a class="internal-link" href="{{ site.baseurl }}{{ note.url }}">Keep Reading</a></p>
{% endfor %}

<hr>

Writing

<ul class="writing">
  {% assign recent_notes = site.notes | sort: "last_modified_at_timestamp" | reverse %}
  {% for note in recent_notes limit: 5 %}
    <li>
      <a class="internal-link" href="{{ site.baseurl }}{{ note.url }}">
        <div class="flex baseline"> <span class="faint small">{{ note.last_modified_at | date: "%d-%m-%Y" }}</span> {{ note.title }}</div>
        </a>
    </li>
  {% endfor %}
</ul>
