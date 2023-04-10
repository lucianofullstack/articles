---
title: "Star Rating using CSS"
date: 2023-04-10
categories: CSS
tags: snippets html css rating
---

## GOAL

Create a rating system using minimum HTML.

## HTML

In orther to specify a rating we will use a `span` with a <a href="https://developer.mozilla.org/en-US/docs/Learn/HTML/Howto/Use_data_attributes">`data attribute`</a> and a value from `1` to `5`.

```
<span class="star" data-rating="3"></span>
```

## CSS

The whole purpose of this snippets it´s to try to practice selectors and how can we use CSS to represent information from a <a href="https://developer.mozilla.org/en-US/docs/Learn/HTML/Howto/Use_data_attributes">data attribute</a>.

### The Content

We are going to use the `★` character for our rating system. 

1. <span style="color:#ffc700">★</span><span style="color:#dddad7">★★★★</span>

2. <span style="color:#ffc700">★★</span><span style="color:#dddad7">★★★</span>

3. <span style="color:#ffc700">★★★</span><span style="color:#dddad7">★★</span>

4. <span style="color:#ffc700">★★★★</span><span style="color:#dddad7">★</span>

5. <span style="color:#ffc700">★★★★★</span>

### The Logic

If you think about it we are always to show <strong>five stars</strong>, some will be <span style="color:#ffc700">★</span>, and others will be <span style="color:#dddad7">★</span>. 

In orther to show both types we will use the `::before` (<span style="color:#ffc700">★</span>) and `::after` (<span style="color:#dddad7">★</span>) selectors.

Rating | before | after
:----: | :-----:|:----:
1      | 1      | 4
2      | 2      | 3
3      | 3      | 2
4      | 4      | 1
5      | 5      | 0

Now we know how many stars will our content need and we can group them.

Content | before | after
:-----: | :-----:|:----:
1 ★     | 1      | 4
2 ★     | 2      | 3
3 ★     | 3      | 2
4 ★     | 4      | 1
5 ★     | 5      | 0

### The Code

`
.star[data-rating="1"]::before,
.star[data-rating="4"]::after {
  content: "★";
}
.star[data-rating="2"]::before,
.star[data-rating="3"]::after {
  content: "★★";
}
.star[data-rating="3"]::before,
.star[data-rating="2"]::after {
  content: "★★★";
}
.star[data-rating="4"]::before,
.star[data-rating="1"]::after {
  content: "★★★★";
}
.star[data-rating="5"]::before,
.star[data-rating="0"]::after {
  content: "★★★★★";
}
`

## Example

<p class="codepen" data-height="300" data-default-tab="html,result" data-slug-hash="VwELpPO" data-user="lucianofullstack" style="height: 300px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/lucianofullstack/pen/VwELpPO">
  star rating</a> by Luciano Pereira (<a href="https://codepen.io/lucianofullstack">@lucianofullstack</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>

<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>