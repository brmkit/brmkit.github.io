---
layout: default
---

## projects

<ul class="project-list">
    {% assign projects = site.data.projects %}
    {% for project in projects %}
    <li class="project-item">
        <div>
            <a href="{{ project.url }}" class="project-link" target="_blank">{{ project.name }}</a>
        </div>
        <small>{{ project.description }}</small>
    </li>
    <div style="margin-bottom: 15px;"></div>
    {% if forloop.last %}</ul>{% endif %}
    {% endfor %}