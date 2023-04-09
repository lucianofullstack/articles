---
layout: page
title: "Test Page"
permalink: /test
---

# Test Page

baseurl: "" # the subpath of your site, e.g. /blog
url: "" # the base hostname & protocol for your site, e.g. https://example.com

# defaults:
#   home:
#     banner: "Your image url"


# code_badge:
#   enabled: "true"
#   color: "#fff"
#   background_color: "#ff4e00"
#   text_transform: "uppercase"  # ("uppercase", "lowercase", "capitalize")

# Banner default settings
# These banner settings are for global banner default, but you can also
# config it by the front matter for one specific post
# banner:
#   video: null             # Video banner source
#   loop: true              # Video loop
#   volume: 0               # Video volume (100% is 1.0)
#   start_at: 0             # Video start time
#   image: null             # Image banner source
#   opacity: 1.0            # Banner opacity (100% is 1.0)
#   background: "rgba(0, 0, 0, 0.8)"  # Banner background (Could be a image)
#   height: "640px"         # Banner default height
#   min_height: null        # Banner minimum height
#   heading_style: null     # Custom heading style (e.g. "font-weight: bold; text-decoration: underline")
#   subheading_style: null  # Custom subheading style (e.g. color: gold)


# Build settings
# highlighter: none
markdown: kramdown
kmarkdown:
  input: GFM

plugins:
  - jekyll-feed
  - jekyll-seo-tag
  - jekyll-sitemap
  - jekyll-paginate
  - jekyll-spaceship

category-list: [code, blog, unix]

<ul>
  {% for post in site.posts %}
    <li>
      <a href="{{site.baseurl}}{{ post.url }}">{{ post.title }}</a>
    </li>
  {% endfor %}
</ul>

<ul>
  {% for category in site.categories %}
    {% capture category_name %}{{ category | first }}{% endcapture %}
      <a href="{{site.baseurl}}{{category_name}}">{{category_name}}</a>
  {% endfor %}
</ul>



