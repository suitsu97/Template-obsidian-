---
Title: "{{title | escape}}"
Year: {{date | format("YYYY")}}
Authors: {{authors}}
Tags: {% if allTags %}{{allTags}}{% endif %}
---

# Reference

{{bibliography}}
{% if abstractNote %}

# Summary

{{abstractNote}}
{% endif %}

# Notes 

{% for annotation in annotations %} 
{% if annotation.annotatedText %} 
{% if annotation.color %} 
<mark class="hltr-{{annotation.colorCategory | lower}}">{{annotation.annotatedText | safe}}</mark> (p. {{annotation.pageLabel}})
{% else %} 
{{annotation.annotatedText | safe}} (p. {{annotation.pageLabel}})
{% endif %} 
{% endif %} 

{% if annotation.comment %} 
> {{annotation.comment | safe}} (p. {{annotation.pageLabel}})
{% endif %} 

{% if annotation.imageRelativePath %} 
![Area Selection]({{annotation.imageRelativePath}})
{% elif annotation.image %} 
![Area Selection]({{annotation.image}})
{% endif %} 

{% if annotation.allTags %}
{% for tag in annotation.allTags.split(',') %}#{{ tag | trim }} {% endfor %}
{% endif %}

--- 

{% endfor %}