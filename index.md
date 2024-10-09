---
layout: default
---

## whoami

<img class="profile-picture" src="https://avatars.githubusercontent.com/u/29227228?v=4">

You'r right, it’s `#ae0001` **_just another redteamer’s blog_** `#ae0001`, nothing more.

## recent posts
<ul class="recent-posts">
    {% assign blog_posts = site.posts | where: 'blog_post', true %}
    {% if blog_posts.size == 0 %}
        <li class="no-posts">
            <h4>
                <a class="una" href="">
                    <span>coming soon!</span>
                </a>
            </h4>
        </li>
        </ul>
    {% else %}
        {% for post in blog_posts limit:3 %}
            <li class="posts-list">
                <h4>
                    <div style="display: inline-block; width: 90px">
                        <small>{{ post.date | date: "%Y-%m-%d" }}</small>
                    </div>
                    <a class="una" href="{{ site.baseurl }}{{ post.url }}">
                        <span>{{ post.title }}</span>
                    </a>
                </h4>
            </li>
            {% if forloop.last %}</ul>{% endif %}
        {% endfor %}
    {% endif %}

## projects

<ul class="project-list">
    {% assign projects = site.data.projects %}
    {% for project in projects %}
    <li class="project-item">
        <div>
            <a href="{{ project.url }}" class="project-link" target="_blank">{{ project.name }}</a>
        </div>
    </li>
    {% if forloop.last %}</ul>{% endif %}
    {% endfor %}

> [!CAUTION]
>Is this another wannabe redteamer's blog with a bunch of technical articles, findings and some dark magic? 
>yes, otherwise I would probably delete it.