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

The best place to start off learning anything new is to check out the documentation. If it is a well-established source, it'll surely contain some form of 'Hello-World' program. Jekyll's website seems to have substantial documentation which was super newbie friendly. I started with the [quickstart](https://jekyllrb.com/docs/) guide, which consisted of a  couple of fairly straightforward commands, after the installation of [Ruby](https://jekyllrb.com/docs/installation/). At first, I was confused seeing two Ruby stable versions on the download page. I ended up with the lesser of the two keeping in mind that my theme was fairly old, so the more bleeding edge version of ruby, the more likely I'll have troubles setting the Jekyll blog up.I ended up following the instructions through, and spinning up a default blog. To my surprise, the blog looked really good in it's minimal glory. To add to it, I was taken aback on how simple it was to get started, unlike WordPress where one needed to setup XAMPP or get a custom third-party software to spin up an instance.

The following is a simple Jekyll structure, when you initialise an empty directory, with the assumption of following the quickstart guide on Jekyll's website.
<pre><code class="plaintext">
myblog
  |- _posts
  |- _site
  |- .gitignore
  |- _config.yml
  |- 404.html
  |- about.md
  |- GemFile
  |- Gemfile.lock
  |- index.md
</code></pre>

At this point, I was slightly lost in what could all these folders/files possibly mean. From my experiences, I've known to learn basics quickly from video tutorials and then get to the advanced part with the help of the documentation. I searched YouTube, and found this great tutorial by [GiraffeAcademy](https://www.youtube.com/watch?v=T1itpPvFWHI&list=PLLAZ4kZ9dFpOPV5C5Ay0pHaa0RJFhcmcB), which worked wonders.

Let's start off with the "_posts" folder. This, as the name suggests, is the folder where all the posts reside. If you do notice from the sample, the posts are all written in ".md" format, or [MarkDown](https://guides.github.com/features/mastering-markdown/). The "_site" folder consists of the rendered site, when you run a 'jekyll serve' command. I wont be going in-depth about the basics of Jekyll, since there are ample of tutorials out there describing what liquid templating, front matter and the various other esoteric terms are. Instead, I'll be focusing on my thought-process of taking an off-the-self theme and customizing it to my liking.

<hr>
## **Fixing A Broken Theme**
<hr>
{% include media-image.html folder=images_folder file="a_broken_theme-selecting_a_blogging_platform_ii.jpg" title="A Broken Theme" caption="Repairing off-the-shelf theme" %}
The theme upon "Jekyll Serving", seemed to work fine in Mozilla Firefox. Every theme is expected to run straight out-of-the-box when purchased, since you are paying a premium for it. Unfortunately, I knew something had to be amiss, since this theme was made during the initial years of Jekyll's popularity. Upon checking cross-browser compatibility, I found out that the theme broke on Google Chrome. This led me spiralling down a number of fixes and customisations to an otherwise very satisfying theme.

My past experience with cross-browser compatibility always stated that it's surely some Javascript that is messing up the images from rendering. After some hacking around, I seem to have found the culprit. Under the "_include" folder (the folder that contains snippings that are stitched together at runtime to render one's page) consited of a footer.html, for including all Javascript which the page uses. To my surprise, it contained the following code:

<pre><code class="html">
{% raw %}
&lt;script src="{{ '/assets/jquery-2.1.1...."&gt;&lt;/script&gt;
&lt;script src="{{ '/assets/viewportchecker.js..."&gt;&lt;/script&gt;
{% endraw %}
</code></pre>

Well, that's a problem. This would only mean that I have a blog which would <i>NEVER</i> update jquery and it's corresponding libraries. Plus, since this would be a disk read, it would be slower than a CDN. Time to change all these links to refer to a CDN rahter than local files!

<pre><code class="html">
{% raw %}
&lt;script src="https://code.jquery.com/..."&gt;&lt;/script&gt;
&lt;script src="https://cdnjs.cloudflare.com/..."&gt;&lt;/script&gt;
{% endraw %}
</code></pre>

Thankfully, that ended up repairing the theme, and I did not have to do much hacking within viewport.js to get things running for chrome. However, this got me intrested in googling more and making the theme more to my linking.

<hr>
## **A New Navigation System**
<hr>
{% include media-image.html folder=images_folder file="a_new_navigation_system-selecting_a_blogging_platform_ii.jpg" title="Changing the Navigation" caption="Adding a search instead of a menu" %}