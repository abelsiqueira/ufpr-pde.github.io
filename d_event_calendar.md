---
layout: page
title: Events
permalink: /events/
---

Here is a list of events of interest for the optimization community.
To submit an event to this list see our
[guide]({{ site.baseurl }}/2016/01/26/new-events.html).

Usual places to look for next events:
- [SIAM calendar](http://siam.org/meetings/calendar.php)
- [EURO calendar](https://www.euro-online.org/web/pages/460/calendar)

{% assign events = site.data.events | sort: 'date' %}
{% for event in events %}
<div class="card container-fluid">
<h4 id="{{event.key}}">
<a href="#{{ event.key }}"></a>
<a href="{{ event.url }}">
{% if event.acro %}
  <strong> {{ event.acro }} </strong> -
{% endif %}
{{ event.name }}
</a>
</h4>
<p>
<strong> {{ event.venue }} </strong> <br>
{% if event.dateend != event.date %}
  {% assign SD = event.date | date: "%d" %}
  {% assign SM = event.date | date: "%b" %}
  {% assign ED = event.dateend | date: "%d" %}
  {% assign EM = event.dateend | date: "%b" %}
  <!-- assuming no event is happening trough the new year's day -->
  {% assign Y = event.date | date: "%Y" %}
  {% if SM == EM %}
  <strong> {{ SM }} {{ SD }}-{{ ED }}, {{ Y }} </strong>
  {% else %}
  <strong> {{ SM }} {{ SD }}-{{ EM }} {{ ED }}, {{ Y }} </strong>
  {% endif %}
{% else %}
  <strong> {{ event.date | date: "%b %d, %Y" }}. </strong>
{% endif %}
{% if event.datesub %}
<em> Submissions end
on {{ event.datesub | date: "%b %d, %Y" }}</em>
<br>
{% endif %}
{% if event.url %}
More information on the
<a href="{{ event.url }}">site</a>.
{% else %}
We don't have a site for this event.
If you know the site, please submit to us.
{% endif %}
</p>
</div>
{% endfor %}
