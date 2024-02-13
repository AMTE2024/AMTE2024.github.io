---
layout: default
---

{% assign talk = site.data.keynote %}
{% assign speaker = talk.speaker %}

{% if talk %}
# Keynote talk

## Speaker

{% if speaker.photo %}
![{{ speaker.name }}]({{ speaker.photo }})
{% endif %}

### {{ speaker.courtesy_title }} {{ speaker.name }}, {{ speaker.affiliation }}, {{ speaker.country }}

{{ speaker.bio }}

{% if talk.title and talk.abstract %}
### {{ talk.title }}

{{ talk.abstract }}


{% if talk.materials %}
### Materials

{% for material in talk.materials %}
* [{{ material.title }}]({{ material.url }})
{% endfor %}
{% endif %}

{% endif %}

{% else %}
The keynote talk has not been announced yet.
{% endif %}
