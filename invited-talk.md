---
layout: default
---

{% if site.data.invited_talk %}
# Invited talk

## Speaker

{% assign speaker = site.data.invited_talk.speaker %}
![{{ speaker.name }}]({{ speaker.photo }})

### {{ speaker.courtesy_title }} {{ speaker.name }}, {{ speaker.affiliation }}, {{ speaker.country }}

{{ speaker.bio }}

{% assign talk = site.data.invited_talk %}
### {{ talk.title }}

{{ talk.abstract }}

{% else %}
No invited talk has been announced yet.
{% endif %}
