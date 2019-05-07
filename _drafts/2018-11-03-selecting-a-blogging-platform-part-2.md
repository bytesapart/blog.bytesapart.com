---

layout: default
title: Selecting a Blogging Platform - Part II
type: post
navigation: false

date:           2018-11-03 00:12:05
excerpt:         This post describes the technical challenges I faced when modifying an off-the-shelf theme to my liking, and using those experiences to learn technologies that make the internet run.
categories:        programming
gradient:         3
image:             selecting_a_blogging_platform_ii.jpg
details:        false
permalink: "/selecting-a-blogging-platform-part-ii/"

author:         Osama Iqbal
bio:             Data is always in a state of quantum superposition unless observed upon by visualisations.
twitter:         "http://twitter.com/bytesapart"
linkedin:         "https://www.linkedin.com/in/osamaiqbal/"
rss:             "https://www.bytesapart.com/feed.xml"

---
{%- capture images_folder -%}
    {{ page.permalink }}
{%- endcapture -%}

It's been almost 8 months since my last blog post. Work commitments and balancing academic progress in my Masters in [Quantitative Finance](https://wqu.org/), unfortunately, ate up all my spare time, leading me to push learning new technologies and posting on my blog onto the backseat. As my academic session comes to a close, I happen to have freed up that time slot for doing regular blog posts with fixed time frames and working on a side-projects concerning what I love doing the most, that is, teaching!

That said, this post is a continuation of the [first part](https://www.bytesapart.com/selecting-a-blogging-platform/), where I describe what led me to choose Jekyll as a blogging platform. This post pertains mostly to the technical aspects of buying some off-the-shelf component, modifying it to one's liking and the challenges one faces in doing so.

<hr>
## **The Jekyll System**
<hr>
{% include media-image.html folder=images_folder file="the_jekyll_structure-selecting_a_blogging_platform_ii.jpeg" title="Jekyll Structure" caption="Understanding Jekyll's file structure" %}
At this point, I wasn't familiar with any of the cool, new stuff coming out from Javascript. For me, this 'template' style programming was completely new. Nonetheless, since Jekyll seemed to be the most convenient option that I had, I decided to dive straight into it.

The best place to start off learning anything new is to check out the documentation. If it is a well-established source, it'll surely contain some form of 'Hello-World' program. Jekyll's website seems to have substantial documentation which was super newbie friendly. I started with the [quickstart](https://jekyllrb.com/docs/) guide, which consisted of a  couple of fairly straightforward commands, after the installation of [Ruby](https://jekyllrb.com/docs/installation/). At first, I was confused seeing two Ruby stable versions on the download page. I ended up with the lesser of the two keeping in mind that my theme was fairly old, so the more bleeding edge version of ruby, the more likely I'll have troubles setting the Jekyll blog up.
