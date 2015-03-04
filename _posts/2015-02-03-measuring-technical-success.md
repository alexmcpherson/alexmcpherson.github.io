---
layout: post
title: "Measuring Technical Success (Is Hard)"
modified:
categories: ['management']
excerpt: Measuring a developer's success is tricky. It's well documented that any kind of performance measuring is ripe for being gamed. What should you do as a manager?
tags: ['management']
image:
  feature:
date: 2015-02-03T19:24:23-07:00
---

###_Mirrored from quickleft.com_###


Measuring a team or single developer's success is tricky. It's well documented that any kind of performance measuring is ripe for being gamed. You spend weeks evaluating and hiring only the smartest people available; they know how to bump up their numbers.

So how do you determine if a team is firing on all cylinders? Let's start with some bad ideas:

1. Count commits, lines changed, SLOC, or other raw code metrics<br /> <em>The result is your codebase growing towards those metrics. Not good.</em>

2. Communication flow (emails sent and read, IRC messages posted, etc)<br /> <em>Some tasks require dedicated headphone time with nothing but vim open, while others need collaboration across teams. This could be quite inaccurate.</em>

3. Butt-in-chair time<br /> <em>Nothing diminishes an knowledge worker's value than only measuring their physical presence</em>

<blockquote>

"This is somewhere I think we have to admit to our ignorance." - <a href="http://martinfowler.com/bliki/CannotMeasureProductivity.html">Martin Fowler</a>
</blockquote>


<hr />

So you need to be careful what you measure. The well known adage says what you measure will improve, so my position is that <em>evaluating team's contribution to business <abbr title="Key Performance Indicators">KPIs</abbr></em> is the only useful way to evaluate their contribution to your company. A perfectly composed, well tested class hierarchy is useless if your company is out of runway. The best teams will easily straddle that divide between avoiding technical debt and shipping useful features to users.

As an example: one of the hardest things to do in software is to estimate progress in a predictable way. If you use a piece of project management software like Sprint.ly, this is actually pretty easy to tease out of historical data:

<img src="/images/cycle-time.png" alt="" />

Here is some anonymized data on how long a developer averages in moving a story from 'ready' to 'accepted'. There are some other factors you might want to see in here like average size of story started (does the slower person just choose very large stories?), but this is a good start in fingerprinting your team and its behavior with business metrics. Who might you want to check in with? Who from this chart might merit praise? If you have a solid process of writing, grooming, and sizing stories, this sort of measurement is hard to game and the numbers fall naturally out of a team's development cycle.

Measuring a team using JUST these numbers is silly, and should only be used as ancillary data that gets augmented by your close relationship with everyone on your team. Having some data points can let you start to see motion in one direction or another, and relative measure between teams or people, but don't forget your strongest asset: your relationship with your team.

As those whiskers get shorter your product owners can be more accurate in their commitments and you can reliably plan the future of your company and product. Huge win!

Other potential business KPIs that can be tied back to a technical team might include a mix of release markers, account churn, customer happiness ratings, bug and crash rates, or adoption and usage of a new feature.