---
layout: default
---

# Panel

## Moderator

{% assign mod = site.data.panel.moderator %}
{% if mod %}
* {{ mod.name }}, {{ mod.affiliation }}, {{ mod.country }}
{% else %}
The moderator has not been announced yet.
{% endif %}

## Panelists

{% if site.data.panel.panelists %}
{% for panelist in site.data.panel.panelists -%}
* {{ panelist.name }}, {{ panelist.affiliation }}, {{ panelist.country }}
{% endfor %}
{% else %}
Panelists have not been announced yet.
{% endif %}

## Panel's chosen questions

{% if site.data.panel.questions %}
{% for question in site.data.panel.questions %}
* {{ question.q }}
    {%- if question.followups -%}
    {% for followup in question.followups %}
    * {{ followup }}
    {%- endfor -%}
    {%- endif -%}
{% endfor %}
{% else %}
No questions have been chosen yet.
{% endif %}

## Outline

{% if site.data.panel.outline %}
{% for item in site.data.panel.outline %}
* {{ item }}
{%- endfor -%}
{% else %}
Panel outline has not been announced yet.
{% endif %}
