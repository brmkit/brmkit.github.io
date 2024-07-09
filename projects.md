---
layout: default
---

## projects

<ul class="project-list">
    {% for project in site.data.projects %}
    <li class="project-item">
        <div style="display: inline-block; width: 90px">
            <a href="{{ project.url }}" class="project-link" target="_blank">{{ project.name }}</a>
        </div>
        <small>{{ project.description }}</small>
    </li>
    {% if forloop.last %}</ul>{% endif %}
    {% endfor %}