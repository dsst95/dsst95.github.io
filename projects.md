---
title: pages.projects
permalink: /
pagination:
  enabled: true
repos: ["PILOS", "STM32-Getting-Started", "Vulnerable-Server", "ADC_EMBS_WS2019-20_Stumm_5217157", "R-cluster
", "Patientmanager", "Brainworks", "PassKeeper", "Snake"]
---

<div class="posts-list">
  {% assign filtered_repos = site.github.public_repositories | where_exp:"repository", "page.repos contains repository.name" %}
  {% for repository in filtered_repos %}
    <a href="{{ repository.html_url }}">
    <div class="post">
      <img src="https://opengraph.githubassets.com/1/{{repository.owner.login}}/{{repository.name}}" class="post-figure" />
      <div class="post-title" title="{{ repository.name | escape  }}">{{ repository.name | escape }}</div>
      <div class="post-text" title="{{ repository.description | escape }}">{{ repository.description | escape }}</div>
      <div class="post-footer">
        <div class="post-author">{% avatar {{repository.owner.login}} size=25 %} {{repository.owner.login}}</div>
        {{repository.license.spdx_id}}
        <div class="post-date">{{ repository.updated_at | date_to_string }}</div>
      </div>
    </div>
    </a>
  {% endfor %}
</div>
