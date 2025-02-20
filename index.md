---
title: pages.blog
permalink: /
pagination:
  enabled: true
---

<div class="posts-list">
  {% for post in site.posts %}
    <a href="{{ post.url }}">
    <div class="post">
    {% if post.image != "" %}
      <img src="{% link {{ post.image }} %}" class="post-figure" />
    {% else %}
      <img src="{% link /assets/images/NoImage.webp %}" class="post-figure" />
    {% endif %}
      <div class="post-title" title="{{ post.title }}">{{ post.title }}</div>
      <div class="post-text" title="{{ post.excerpt }}">{{ post.excerpt }}</div>
      <div class="post-footer">
        <div class="post-author">{% avatar dsst95 size=25 %} {% t common.name %}</div>
        <div class="post-date">{{ post.date | date_to_string }}</div>
      </div>
    </div>
    </a>
  {% endfor %}
</div>

{% if paginator.total_pages > 1 %}
<div class="pagination">
  {% if paginator.previous_page %}
    <a href="{{ paginator.previous_page_path | prepend: site.baseurl | replace: '//', '/' }}">&laquo;</a>
  {% else %}
    <span>&laquo;</span>
  {% endif %}

  {% for page in (1..paginator.total_pages) %}
    {% if page == paginator.page %}
      <span class="page">{{ page }}</span>
    {% elsif page == 1 %}
      <a href="{{ paginator.previous_page_path | prepend: site.baseurl | replace: '//', '/' }}">{{ page }}</a>
    {% else %}
      <a href="{{ site.paginate_path | prepend: site.baseurl | replace: '//', '/' | replace: ':num', page }}">{{ page }}</a>
    {% endif %}
  {% endfor %}

  {% if paginator.next_page %}
    <a href="{{ paginator.next_page_path | prepend: site.baseurl | replace: '//', '/' }}">&raquo;</a>
  {% else %}
    <span>&raquo;</span>
  {% endif %}
</div>
{% endif %}
