---
layout: default
---

{% assign talk = site.data.invited_talk %}
{% assign speaker = talk.speaker %}

{% if talk %}
# Invited talk

## Speaker

{% if speaker.photo %}
![{{ speaker.name }}]({{ speaker.photo }})
{% endif %}

### {{ speaker.courtesy_title }} {{ speaker.name }}, {{ speaker.affiliation }}, {{ speaker.country }}

{{ speaker.bio }}

{% if talk.title and talk.abstract %}
### {{ talk.title }}

{{ talk.abstract }}

* [Slides](/assets/slides/ChapelForAMTE2022.pdf)


{% endif %}

{% else %}
No invited talk has been announced yet.
{% endif %}
