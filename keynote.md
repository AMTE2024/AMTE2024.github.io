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

* [Slides](/assets/slides/cpp_standard_parallelism__r8__2023_europar_amte.pdf)
* [Video](https://youtu.be/azKOE-8Inkw)

{% endif %}

{% else %}
The keynote talk has not been announced yet.
{% endif %}
