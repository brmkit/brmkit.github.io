---
layout: default
---

## whoami

<img class="profile-picture" src="https://avatars.githubusercontent.com/u/29227228?v=4">

I’ve been passionate about **offensive security** for years, dedicating a lot of time and energy to stay ahead in this ever-evolving field. My main focus is on **adversary emulation** and **red teaming**, areas that are always pushing the limits and challenging me to grow. Every day, *I’m all about learning, testing, and refining my skills*.

To keep advancing, I use my personal *homelab* as my playground for security research. It’s where I keep my skills sharp and experiment with new tools and techniques, showcasing my genuine enthusiasm for this field.

The aim of this blog/site it's simple, *to share what I’m learning, discovering, and finding useful*. Obviously not in my native language, *because I really like to smash my head on something while i'm trying to be better in english.*

I don’t see myself as an expert who has *“made it”*, but rather as someone on a journey: *always improving, always curious*.

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

## nerdy vanity
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


### activities
I also enjoy partecipating in Capture the Flag competitions and challenging myself in "_complex_" environment like:

Year | Provider | Labs
-----|-------|--------
2024 | [VulnLab - Labs](https://www.vulnlab.com/main/red-team-labs) | Wutai Master
2023 | [HackTheBox - ProLabs](https://www.hackthebox.com/hacker/pro-labs) | Rastalabs - Red Team Operator I
2021 | [HackTheBox - ProLabs](https://www.hackthebox.com/hacker/pro-labs) | Offshore - Penetration Tester II