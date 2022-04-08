---
layout: default
---

{% if site.data.invited_talk %}
# Invited talk

## Speaker

{% assign speaker = site.data.invited_talk.speaker %}
{% if speaker.photo %}
![{{ speaker.name }}]({{ speaker.photo }})
{% endif %}

### {{ speaker.courtesy_title }} {{ speaker.name }}, {{ speaker.affiliation }}, {{ speaker.country }}

{{ speaker.bio }}

{% assign talk = site.data.invited_talk %}
{% if talk.title and talk.abstract %}
### {{ talk.title }}

{{ talk.abstract }}
{% endif %}

{% else %}
No invited talk has been announced yet.
{% endif %}
