---
layout: default
---

# Organizing Committee

{% for member in site.data.committee.organizing -%}
* {{ member.name }}, {{ member.affiliation }}, {{ member.country }}
{% endfor %}

# Program Committee 

{% for member in site.data.committee.program -%}
* {{ member.name }}, {{ member.affiliation }}, {{ member.country }}
{% endfor %}
