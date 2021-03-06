---
title: How to build components within Craft CMS
date: 2018-09-12T09:27:34
description: In this screencast I demonstrate how to move repeatable HTML elements into reusable components for portability.
tags:
  - craftcms
  - screencast
---
{% Youtube "FNIM8MvUL-Q" %}

It is typically best practice to not repeat yourself. Keep it DRY. In this screencast I demonstrate how to move repeatable HTML elements into reusable components for portability.

An added benefit of working in this way is being able to mock data across templates before you get into setting up the CMS like you can see below.

{% verbatim %}
```twig
{# templates/_components/card.twig #}

<article class="c-card">
  <h2>{{ title }}</h2>
  <p>{{ description }}</p>
</article>
```
{% endverbatim %}

{% verbatim %}
```twig
{% set cards = [
  {
    title: "Card Title 1",
    description: "Card description would go here."
  },
  {
    title: "Card Title 2",
    description: "Card description would go here."
  }
] %}

{% for card in cards %}
  {% include '_components/card' with {
    title: card.title,
    description: card.description
  } %}
{% endfor %}
```
{% endverbatim %}

Now once your CMS is setup you can remove the temporary data and update the reference to cards to pull from the CMS.
