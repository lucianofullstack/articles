---
title: "Star Rating using CSS"
date: 2023-04-10
categories: CSS
tags: snippets html css rating
---

## The GOAL

Create a rating system using minimum HTML.

## The HTML

In orther to specify a rating we will use a `span` with a <a href="https://developer.mozilla.org/en-US/docs/Learn/HTML/Howto/Use_data_attributes">`data attribute`</a> and a value from `1` to `5`.

```
<span class="star" data-rating="3"></span>
```

## The CSS

We are going to use the `★` character for our rating system. 

<span style="color:#ffc700">★★★★★</span>

<span style="color:#ffc700">★★★★</span><span style="color:#dddad7">★</span>

<span style="color:#ffc700">★★★</span>
<span style="color:#dddad7">★★</span>

<span style="color:#ffc700">★★</span>
<span style="color:#dddad7">★★★</span>

<span style="color:#ffc700">★</span>
<span style="color:#dddad7">★★★★</span>


If you think about it we are always to show five stars, some will be 


and the `::before` and `::after` selectors in order to define how many stars are going to be turned on ★
★

## Example

<p class="codepen" data-height="300" data-default-tab="html,result" data-slug-hash="VwELpPO" data-user="lucianofullstack" style="height: 300px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/lucianofullstack/pen/VwELpPO">
  star rating</a> by Luciano Pereira (<a href="https://codepen.io/lucianofullstack">@lucianofullstack</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>

<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>