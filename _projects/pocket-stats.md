---
title: Pocket Stats
layout: project
thumbnail: pocket-stats.jpg
github: pocket-analytics
type: personal
excerpt: Keeping Track of My Pocket Queue
priority: 40
---

Curious about how much I was falling behind in my [Pocket](https://getpocket.com/about/) reading list, I decided to graph the amount of articles in it.

<p>Right now, the project is built on D3 and Laravel. Through the use of a cron job, the application can query the Pocket servers and compare them against the last entry made, if the two numbers are different, and through my RESTful api I can add and control existing points.</p>

<p>The project is still in development, but when completed it should have a nicer graph that contains more information, uses AngularJS, and allow other users to track their own progress.</p>

<p>Update: I pulled down the project as I became too obsessed with lowering my total count.</p>

![Old image of the project]({{ site.url }}/assets/images/content/sized/pocket-stats/overview-large.jpg)
_Old image of the project, before I pulled it down_