---
title: Welcome to my github
---


<ul>
  {% for post in site.posts %}
    <li>
      <a href="{{site.baseurl}}/{{ post.url }}">{{ post.title }}</a>
    </li>
  {% endfor %}
</ul>

<ul>
  {% for category in site.categories %}
    {% capture category_name %}{{ category | first }}{% endcapture %}
      <a href="{{site.baseurl}}/{{category_name}}">{{category_name}}</a>
  {% endfor %}
</ul>


{% for tag in site.tags %}
  <h3>{{ tag[0] }}</h3>
  <ul>
    {% for post in tag[1] %}
      <li><a href="{{site.baseurl}}/{{ post.url }}">{{ post.title }}</a></li>
    {% endfor %}
  </ul>
{% endfor %}

