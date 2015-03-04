---
layout: post
title: "When to Level Up Your JavaScript"
modified:
categories: ['code']
excerpt: Some applications use lots of JavaScript, others not so much. When to add things like testing and an MVC framework are hard choices to make. I'll help you!
tags: ['code', 'javascript']
image:
  feature:
date: 2015-03-03T09:39:46-07:00
---

###_Mirrored from quickleft.com_###


Websites grow in fits and starts, often with different owners and contributors over time. Some features are made in a time crunch where others had time for planning and testing. There are some excellent strategies to help keep JavaScript fast, free of regressions, organized, and well tested. They are sometimes overkill for a smaller project, which leads us to <strong>The Problem</strong>:

<blockquote>
Right-sizing your JavaScript tooling from the get-go is impossible, because projects grow in unpredictable ways
</blockquote>

So with that out of the way, how do you figure out your growth plan for your project? When do you add <a href="http://www.gruntjs.com">Grunt</a> or <a href="http://www.gulpjs.com">Gulp</a>? Speed is always a priority for a developer, so if you slow down to add tooling and don't see benefits, you've made the wrong choice.

I have a framework of JavaScript tools and strategies and an associated 'pain point' that indicates an upgrade is in order. If you're feeling that pinch, now is the time to refine how you write your JavaScript.

####Unnecessary Code Running on a Page

You keep adding plugins, and kicking them off inside a giant <code>$(document).ready</code> function. "But this page doesn't have modals! Why does that even run here..." you say. Well, a solid solution here is to explore options for organizing your code to run by page. I've had success in the past using just the <code>Backbone.Router</code> from <a href="http://www.backbonejs.org%22">Backbone</a> to determined what parts of my code need to be set up. The downside here is introducing a dependency that you possible don't use elsewhere, but the upside is cases where pages behave the same way, and you want to let them share as much code as possible.


Another option is to have a 'core' javascript file containing common functionality for your site, and then have a much smaller series of <code>about-us.js</code> and <code>team.js</code> files that only pick and choose from the core file what functions get run on those pages. The downside here is that you are serving more files, but it is easy to organize.

<hr />

####Developers Keep Breaking Things

This one is easy: start writing tests! Testing is as mature in JavaScript as in other languages, with a complete set of options for <a href="http://nightwatchjs.org/">integration testing</a>, <a href="http://karma-runner.github.io/0.12/index.html">Unit</a> <a href="http://mochajs.org/">testing</a>, <a href="http://sinonjs.org/">stubs, mocks, and spies</a>, and everything else you generally want.

Testing means you need a way to run them, which is often an npm script or Grunt task. If this isn't part of your project, testing usually means you need to add some infrastructure, but it's worth it to make sure your code is running as expected. Testing integrates nicely into a modern deployment workflow that includes continuous integration.

<hr />

####My Page Loads Too Slowly

If you think it is because of your JavaScript, then the answer is a build tool. We like <a href="http://www.gruntjs.com">Grunt</a> and <a href="http://www.gulpjs.com">Gulp</a>, and frameworks like Rails have them built in to some degree.


The benefits here are compressing, uglifying, and minifying your JavaScript to make your payload into one file, and to have that file be much smaller. Typical compression rates can be ~50%, saving a lot of download time for your users.

<hr />

####I Reorder My Script Tags, Hoping Things Will Work

Script tags are generally loaded asynchronously, and evaluated as they are received. One slow connection can mean that your scripts are evaluated in an unpredictable order. For unassociated jQuery plugins this isn't an issue, but as your code gets more complex the resolution order of your scripts becomes key to your site functioning.


This is solvable by introducing a module system to your JavaScript. The two most popular options for client side code are <a href="http://www.requirejs.org">Require.js</a> and <a href="http://browserify.org/">Browserify</a>. They help you write your code as small modules that have dependencies declared. They then resolve those dependencies, put all of your modules into the correct order, and emit a single file that is guaranteed to work in a consistent manner.

<hr />

####Writing HTML in jQuery is Error Prone

It is very common to see DOM manipulation look like:

<pre><code class="">$domNode.html("&lt;div class='" + item.class + "'>" + item.name + "&lt;/div>");</code>
</pre>

Look at those quotes! So hard to keep straight. When you write HTML, you should be writing HTML, not JavaScript. Luckily there are a <a href="http://mustache.github.io/">plethora</a> <a href="http://handlebarsjs.com/">of</a> <a href="http://underscorejs.org/#template">options</a> <a href="http://twitter.github.io/hogan.js/">for</a> <a href="https://github.com/linkedin/dustjs/">client side</a> <a href="http://mozilla.github.io/nunjucks/">templates</a> that can help make your HTML feel more like HTML. In fact, there are <a href="http://garann.github.io/template-chooser/">websites</a> just to help you choose one system!

Our preference at Quick Left is usually <a href="http://underscorejs.org/#template">Underscore</a> or <a href="http://handlebarsjs.com/">Handlebars</a>. They let you write templates that look like this:

<pre><code class="">
{% raw %}&lt;span>{{item.name}}&lt;/span>{% endraw %}
</code></pre>

and then call them like this:

<pre><code class="">$domNode.html( JST.itemRow(item) )
</code></pre>

Much better!

<hr />

####No One Writes Code The Same Way

Some people like semicolons, and some heathens do not. Tabs vs. spaces is a conflict as old as computers, and don't get a developer started on how to name things. This can be exacerbated by lots of people on a project, recent new hires or departures, and a long-lived codebase.

Luckily, a working agreement to use a style guide can address a lot of those problems, as can an automated linting process.

We find JSLint to be too strict and pedantic, so our projects will usually use <a href="http://jshint.com/">JSHint</a> and have a <code>.jshintrc</code> file that specifies how code for this project will be written. By default we will also follow <a href="https://github.com/rwaldron/idiomatic.js/">idiomatic.js</a> on our projects, and adjust our base <code>.jshintrc</code> to reflect those style choices.

Our editors can be set up to show errors as you type them, and our CI process will fail builds if the hint process doesn't pass. This makes it predictable and easy to work on a project, and takes the human element out of most style arguments.

<hr />

Not every project needs every item on this list, but it's important to know that writing JavaScript can and should be a fun, pain free process. If something is adding friction to your development, know that there is probably a tool out there that can east that pain and make it fun again to write in the best of all programming languages, JavaScript.


I presented this framework at jQuery Portland in 2013:

<iframe src="//www.youtube.com/embed/kwSVWlzEefE?rel=0" width="640" height="360" frameborder="0" allowfullscreen="allowfullscreen"></iframe>
