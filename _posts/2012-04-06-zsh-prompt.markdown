---
layout: post
title: "Making your zsh prompt awesome"
modified:
categories: ['code']
excerpt: Having an informative prompt makes your time in the shell more productive. I show you how to add battery life to yours.
tags: ['code']
image:
  feature:
date: 2012-04-06T09:09:46-07:00
---

###_Mirrored from quickleft.com_###

The adoption of FOSS tools for development has meant that a lot of my time is spent at my trusty terminal prompt. I took some time today to make mine a bit more awesome. Quick Left has killer couches, beanbags, spare rooms, and standing desks. This means I'm mobile a lot, and that my battery level is a concern, so I decided to add this to my prompt:

<img src="/images/prompt.png" alt="Battery indicator in prompt" />

I'm using iTerm2, zsh, and oh-my-zsh, as you all should be. The code is posted here as a <a href="https://gist.github.com/2295304">gist</a>, but I'll go ahead and show the fun stuff here:

<p>
<script src="https://gist.github.com/2295304.js">// <![CDATA[

// ]]></script>
</p>

A quick walkthrough: The battery.rb needs to be in a directory that's in your path. I chose <code>usr/local/lib</code>

The encoding is necessary because of the fancy arrow characters. Skip that if you're fine with hyphens. The first two lines backtick to the <strong>P</strong>ower<strong>M</strong>anagement<strong>SET</strong>tings tools, and asks for the battery status. This output is typically:

<code>Currently drawing from 'AC Power'<br /> -InternalBattery-0 85%; charging; 0:23 remaining</code>

A quick one-liner strips out the percentage value, and a color is chosen based on how full the battery is. This is joined into an output string, and that's what gets displayed in the prompt.

Now, like a Roomba, I'll always know when to go back home and charge up. Awesome!