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


### Materials

* [Slides](https://de.slideshare.net/PatrickDiehl3/framework-for-extensible-asynchronous-task-scheduling-feats-in-fortran)

{% endif %}

{% else %}
The keynote talk has not been announced yet.
{% endif %}
