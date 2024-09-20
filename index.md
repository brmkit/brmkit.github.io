---
layout: default
---

## whoami

<img class="profile-picture" src="https://avatars.githubusercontent.com/u/29227228?v=4">

You'r right, it’s **_just another redteamer’s blog_**, nothing more.

I’ve been passionate about **offensive security** for years, dedicating a lot of time and energy to stay ahead in this ever-evolving field. My main focus is on **adversary emulation** and **red teaming**, areas that are always pushing the limits and challenging me to grow. Every day, *I’m all about learning, testing, and refining my skills*.

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

As a bit of background, I can share some of the certifications and training sessions I've attended over the years. This isn't a **comprehensive list**, and I understand that certificates do not prove anything, but... _it's a bit of nerdy vanity_.

Year | What | Title
-----|-------|--------
2024| GCIH | GIAC Certified Incident Handler + GIAC Advisory Board
2024 | Training | [Empire Operations: Tactics (Turla)](https://training.bc-security.org/courses/empire-operations-turla)
2023 | Training | [SpecterOps - Advanced Tactics: Red Team Operations](https://specterops.io/training/red-team-operations/)
2023 | Training | [MalOpSec -> EDR: The Great Escape](https://milano.securitybsides.it/malopsec.html)
2023 | CRTO  | Certified Red Team Operator
2022 | eCPTXv2 | eLearnSecurity Certified Penetration Tester eXtreme v2
2022 | CARTP | Certified Azure Red Team Professional
2020 | CRTP | Certified Red Team Professional
2019 | eJPT | eLearnSecurity Certified Junior Penetration Tester


## activities
I also enjoy partecipating in Capture the Flag competitions and challenging myself in "_complex_" environment:

Year | Provider | Labs
-----|-------|--------
2024 | [VulnLab - Labs](https://www.vulnlab.com/main/red-team-labs) | Wutai Master
2023 | [HackTheBox - ProLabs](https://www.hackthebox.com/hacker/pro-labs) | Rastalabs - Red Team Operator I
2021 | [HackTheBox - ProLabs](https://www.hackthebox.com/hacker/pro-labs) | Offshore - Penetration Tester II

## disclaimer
Is this another wannabe redteamer's blog with a bunch of technical articles, findings and some dark magic? 
> yes, otherwise I would probably delete it.