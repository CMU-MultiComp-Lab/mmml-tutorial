---
layout: schedule
permalink: /schedule/
title: Schedule
---

** Exact topics and schedule subject to change, based on student interests and course discussions. **

{% assign current_module = 0 %}
{% assign skip_classes = 0 %}
{% assign prev_date = 0 %}


<tr class="{{ event_type }}">
    <th scope="row">{{ lecture.part }}</th>
    {% if lecture.title contains 'lectures' %}
    {% assign skip_classes = skip_classes | plus: 1 %}
    <td colspan="4">{{ lecture.title }}</td>
    {% else %}
    <td>
        {{ lecture.title }} <br/>
            <ul>
               {% for topic in lecture.topics %}
                  <li style="font-size:12px;">
                     {{topic}}
                  </li>
               {% endfor %}
        </ul>
    </td>
    <td>
        <ul>
               {% for reading in lecture.readings %}
                  <li style="font-size:12px;">
                     {{reading}}
                  </li>
               {% endfor %}
        </ul>
    </td>
    {% endif %}
</tr>
{% else %}
{% assign current_module = current_module | plus: 1 %}
{% assign module = item %}
<tr class="info">
    <td colspan="5" align="center"><strong>{{ module.title }}</strong></td>
</tr>
{% endif %}
{% endfor %}
