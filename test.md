---
layout: page
title: "Test Page"
permalink: /test
---

# Test Page

baseurl: "" # the subpath of your site, e.g. /blog
url: "" # the base hostname & protocol for your site, e.g. https://example.com
favicon: "" # the favicon for your site

# If you don't want transparent header, you can set false
# 

# If you want to change the content width, you can set to another value
# content_width: "920px"

# Google analytics
# google_analytics: [Tracking ID]

# If you want to generate website sitemap, you can set true
# sitemap: false


# Translate languges
# langs refer to https://cloud.google.com/translate/docs/languages
# translate_langs:
#
#
#   - lang: zh-CN
#     img: https://cdn.countryflags.com/thumbs/china/flag-400.png
#     text: Chinese(Simple)
#
#
#   - lang: ko
#     img: https://cdn.countryflags.com/thumbs/south-korea/flag-400.png
#     text: Korean
#
#   - lang: ru
#     img: https://cdn.countryflags.com/thumbs/russia/flag-400.png
#     text: Russian

# You can choose a theme color
# Default theme colors as below:
# coolblack: #090a0b
# spacegrey: #353535
# snowwhite: #ffffff
# theme_color: snowwhite
# Custom color as below:
# theme_color: "#882250"

# You can choose a brand color
# Default brand colors as below:
# orangered: #ff5100
# greatgold: #f2cb05
# greenblue: #389092
#
# brand_color: orangered
#
# Custom color as below:
# brand_color: "#1a8e42"

# Night/Dark mode
# Default mode is "auto", "auto" is for auto nightshift
# (19:00 - 07:00), "manual" is for manual toggle, and
# "on/off" is for default on/off.
#
# Whatever the user's choice is, it will supersede the
# default setting of the site and be kept during the
# visit (session). Only the dark mode setting is"manual",
# it will be always kept on every visit (i.e. no matter
# the browser is closed or not)
#
# night_mode: "auto"

# Code badge setting
# You can enable or disable the code badge and so on
# code_badge:
#   enabled: "true"
#   color: "#fff"
#   background_color: "#ff4e00"
#   text_transform: "uppercase"  # ("uppercase", "lowercase", "capitalize")

# If you want to link only specific pages in your header, uncomment
# this and add the path to the pages in order as they should show up
# header_pages:
#   - index.html
#   - archives.html
#   - categories.html
#   - tags.html
#   - about.md

# Page default value
# defaults:
#   home:
#     heading: "Your awesome heading"
#     subheading: "Your awesome subheading"
#     banner: "Your image url"

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

# Excerpt size setting
# excerpt_size: 350

# Pagination setting
# paginate: 5

# Disqus comments
# disqus:
#   shortname: "Your Disqus username"

# Gitment comments
# gitment:
#   username: "Your GitHub username"
#   repo: "The repo to store comments"
#   client_id: "Your client ID"
#   client_secret: "Your client secret"
#   redirect_uri: "Your redirect url"   # If you use a custom domain name

# Utterances comments
# See https://utteranc.es/
# set follow_site_theme true to make utterances' theme follow the site's

# utterances:
#   repo: "owner/repo"
#   issue_term: "title"
#   label: "utterances comment"
#   theme: "github-light"
#   follow_site_theme: true

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


{% for tag in site.tags %}
  <h3>{{ tag[0] }}</h3>
  <ul>
    {% for post in tag[1] %}
      <li><a href="{{site.baseurl}}{{ post.url }}">{{ post.title }}</a></li>
    {% endfor %}
  </ul>
{% endfor %}

