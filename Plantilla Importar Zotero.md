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
> {{annotation.annotatedText}} 
 {% endif %} 
 > {% if annotation.comment %} 
 > {{annotation.comment}} 
 > {% endif %} 
 > {% if annotation.imageRelativePath %} ![Area Selection]({{annotation.imageRelativePath}}) {% elif annotation.image %} ![Area Selection]({{annotation.image}}) {% endif %} 
--- 

{% endfor %}