---
layout: default
---

{% if site.data.keynote %}
# Keynote talk

## Speaker

{% assign speaker = site.data.keynote.speaker %}
{% if speaker.photo %}
![{{ speaker.name }}]({{ speaker.photo }})
{% endif %}

### {{ speaker.courtesy_title }} {{ speaker.name }}, {{ speaker.affiliation }}, {{ speaker.country }}

{{ speaker.bio }}

{% assign talk = site.data.keynote %}
{% if talk.title and talk.abstract %}
### {{ talk.title }}

{{ talk.abstract }}
{% endif %}

{% else %}
The keynote talk has not been announced yet.
{% endif %}
