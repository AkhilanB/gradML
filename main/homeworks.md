---
title: "Homeworks"
nav_order: 1
---

# Homeworks

{% assign limit_value = 1 %}  <!-- Set this to the number of hws to display-->
{% assign sorted_homeworks = site.homeworks | sort: 'release_date' | reverse %}
{% assign total_items = sorted_homeworks | size %}
{% assign start_index = total_items | minus: limit_value %}
{% assign filtered_homeworks = sorted_homeworks | slice: start_index, limit_value %}

{% for hw in filtered_homeworks %}
## {{ hw.title }}

- **Release Date:** {{ hw.release_date | date: "%B %d, %Y" }}
- **Due Date:** {{ hw.due_date | date: "%B %d, %Y" }}
- {% if hw.pdf %} **[PDF]({{ hw.pdf }})** {% else %} **PDF:** *To be released* {% endif %}
- {% if hw.gradescope_link %} **[Submit to Gradescope]({{ hw.gradescope_link }})** {% else %} **Submit to Gradescope:** *To be released* {% endif %}

{% endfor %}