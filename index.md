---
layout: default
---


<img class="profile-picture" src="https://avatars.githubusercontent.com/u/29227228?v=4">

You'r right, it’s **_just another redteamer’s blog_**, nothing more.

I’ve been passionate about **offensive security** for years, dedicating a lot of time and energy to stay ahead in this ever-evolving field. My main focus is **adversary emulation** and **red teaming**, areas that are always pushing the limits and challenging me to grow. Every day, *I’m all about learning, testing, and refining my skills*.

To keep advancing, I use my personal *homelab* as my playground for security research. It’s where I keep my skills sharp and experiment with new tools and techniques, showcasing my genuine enthusiasm for this field.

The aim of this blog/site it's simple, *to share what I’m learning, discovering, and finding useful*. Obviously not in my native language, *because I really like to smash my head on something while i'm trying to be better in english.*

I don’t see myself as an expert who has *“made it”*, but rather as someone on a journey: *always improving, always curious*.

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

---

Is this another wannabe redteamer's blog with a bunch of technical articles, findings and some dark magic?
>yes, otherwise I would probably delete it.