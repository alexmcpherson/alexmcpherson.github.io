---
layout: post
title: "How to Perform a CSS Audit"
modified:
categories: ['code']
excerpt: This audit process assesses how organized the project's CSS is, how up to date the pipeline for evaluating and building it is, and how well structured and disciplined the team is that writes the CSS.
tags: ['code', 'css']
image:
  feature:
date: 2015-01-21T19:24:23-07:00
---

###_Mirrored from quickleft.com_###


When we begin work on an existing codebase, one of the first things we will do is a CSS Audit. The main impact of disorganized and poorly maintained CSS are slower development as a team wades through unclear code, and a broken site, as poorly scoped selectors result in collisions and overriding of styles.

This audit process assesses how organized the project's CSS is, how up to date the pipeline for evaluating and building it is, and how well structured and disciplined the team is that writes the CSS. Here are the steps you could use to run your own CSS Audit:

## CSS systems

### What to look for

Does your project have a `CSSReadme` or some similar document that explains how to write CSS for the project? The most successful projects start with a more rigid system like [SMACSS](https://smacss.com/), [BEM](https://bem.info/method/), or [OOCSS](https://github.com/stubbornella/oocss/wiki) and modify it with further suggestions and structure. If this isn't located in a Github repository wiki, the project's main `README`, or in new developer on boarding notes, it's as good as not existing.

At the very least, a CSS system should define:

*   What to name new files, and when to create them
*   How to choose `class` and `id` names
*   What CSS3 properties are supported by the site
*   What syntax options are preferable in the project (are one liners ok?)

### Why it helps

A site's CSS seems to grow at the whims of individual developers. Some will take the time to see if a selector already exists before writing a rule, and others won't. A system takes the guesswork and opinion out of writing CSS, leaving developers just making it look nice, not inventing their own rules.

### First steps to fixing

Have a look through the systems mentioned above and get a feel for their benefits and drawbacks. Talk with the rest of the project team about what they value in their CSS, and choose one that matches your values closely.

The safest way to integrate a new system into an existing website is slowly, one page at a time. New development can be done using the system, and then reusable styles can be backported to the older pages. Also if a redesign is in the pipeline, that is a good opportunity the start fresh with a rewrite. Sometimes that's the only way to be sure.

* * *

## Styleguide

### What to look for

A caring CSS team should have a kitchen sink of the components and styles that comprise their website. When a new developer gets tasked with styling a page, wading through pages of CSS or knowing where to find a reference element in the product isn't always feasible. A style guide is a developer-only page that shows off what styles and components have already been made for the site, so that conventions can be adhered to, time saved, and duplicate styles reduced.

### Why it helps

Having a live page to look at makes it easy to scan for that blue text inside the floating box that is in the comp that just landed on your desk. Not every developer knows the whole website inside and out, so a one-stop shop will encourage that dev to reuse styles instead of just creating it again on their own time.

### First steps to fixing

The next time someone makes a new feature or element, mark it up and style it on a new page somewhere, that has your existing stylesheets included. This will be the seed of your style guide, and try your best to make your elements and components on that page first, to ensure that it display properly in isolation, then bring it over to the page it's meant to be on.

* * *

## Pipeline

### What to look for

Somewhere in your site's documentation should be a description of your asset pipeline, specifically how CSS is handled. There may be a `Gruntfile` indicating tasks that can be run, or you may use a framework like Rails that has a lot of processing built in.

### Why it helps

Writing raw CSS is for the birds. Preprocessors like [Sass](http://sass-lang.com/) and [Less](http://lesscss.org/) take a lot of the pain points out of writing CSS, and encourage good habits with functions and variables.

Before your styles go to production it's important that the CSS is validated in some way. A recent [Quick Left study](http://reports.quickleft.com/css) showed hundreds of made up properties like `colro` and `z-margin` made it to production without being caught. These are mostly harmless, but certainly embarrassing to have on your website and indicative of a lack of attention to detail.

In addition to pre-processing, it's important to the speed of your site to concatenate, and minify your CSS into an asset that can be delivered via a CDN and heavily cached by a browser using the proper cache control headers.

### First steps to fixing

If your framework doesn't natively have a concept of an asset pipeline to process your CSS and JavaScript, try a standalone tool. We like both [Grunt](http://gruntjs.com/) and [Gulp](http://gulpjs.com/). This fits into a larger deploy system, so either building on deploy or ensuring that you build and commit artifacts (the compiled CSS) before you deploy are both viable options with their own benefits and drawbacks.

* * *

Keeping CSS organized and performant is hard, and requires constant attention, often from developers tasked with much 'harder' things like backend features or working in a front end MVC framework. There are tools available to add structure and checks to the process of writing it though, and can help every site get what it deserves: easy to maintain CSS that doesn't get thrown out every few months. The easiest thing to start with from the above list is a simple style guide, so if your site doesn't have that, go ahead and start improving your process today!