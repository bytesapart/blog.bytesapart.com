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

It's been more than a year since my last blog post. Work commitments and balancing academic progress in my Masters in [Quantitative Finance](https://wqu.org/), unfortunately, ate up all my spare time, leading me to push learning new technologies and posting on my blog onto the backseat. As my academic session comes to a close, I happen to have freed up that time slot for doing regular blog posts with fixed time frames and working on a side-projects concerning what I love doing the most, that is, teaching!

That said, this post is a continuation of the [first part](https://www.bytesapart.com/selecting-a-blogging-platform/), where I describe what led me to choose Jekyll as a blogging platform. This post pertains mostly to the technical aspects of buying some off-the-shelf component, modifying it to one's liking and the challenges one faces in doing so.

<hr>
## **The Jekyll System**
<hr>
{% include media-image.html folder=images_folder file="the_jekyll_structure-selecting_a_blogging_platform_ii.jpeg" title="Jekyll Structure" caption="Understanding Jekyll's file structure" %}
At this point, I wasn't familiar with any of the cool, new stuff coming out from Javascript. For me, this 'template' style programming was completely new. Nonetheless, since Jekyll seemed to be the most convenient option that I had, I decided to dive straight into it.

The best place to start off learning anything new is to check out the documentation. If it is a well-established source, it'll surely contain some form of 'Hello-World' program. Jekyll's website seems to have substantial documentation which was super newbie friendly. I started with the [quickstart](https://jekyllrb.com/docs/) guide, which consisted of a  couple of reasonably straightforward commands, after the installation of [Ruby](https://jekyllrb.com/docs/installation/). At first, I was confused seeing two Ruby stable versions on the download page. I ended up with the lesser of the two keeping in mind that my theme was fairly old, so the more bleeding edge version of Ruby, the more likely I'll have troubles setting the Jekyll blog up. I ended up following the instructions through and spinning up a default blog. To my surprise, the blog looked good in its minimal glory. To add to it, I was taken aback on how simple it was to get started, unlike WordPress where one needed to setup XAMPP or get a custom third-party software to spin up an instance.

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

At this point, the possibility of what these files/folders meant made me feel lost. From my experiences, I've known to learn basics quickly from video tutorials and then get to the tricky part with the help of the documentation. I searched YouTube and found this great tutorial by [GiraffeAcademy](https://www.youtube.com/watch?v=T1itpPvFWHI&list=PLLAZ4kZ9dFpOPV5C5Ay0pHaa0RJFhcmcB), which worked wonders.

Let's start with the "_posts" folder, which, as the name suggests, is the folder where all the posts reside. If you do notice from the sample, the posts are all written in ".md" format, or [MarkDown](https://guides.github.com/features/mastering-markdown/). The "_site" folder consists of the rendered site when you run a 'Jekyll serve' command. I won't be going in-depth about the basics of Jekyll since there are ample tutorials out there describing what liquid templating, front matter and the various other esoteric terms are. Instead, I'll be focusing on my thought-process of taking an off-the-shelf theme and customizing it to my liking.

<hr>
## **Fixing A Broken Theme**
<hr>
{% include media-image.html folder=images_folder file="a_broken_theme-selecting_a_blogging_platform_ii.jpg" title="A Broken Theme" caption="Repairing off-the-shelf theme" %}
The theme upon "Jekyll Serving", seemed to work fine in Mozilla Firefox. Every theme is expected to run straight out-of-the-box when purchased since you are paying a premium for it. Unfortunately, I knew something had to be amiss since this theme's inception was during the initial years of Jekyll's popularity. Upon checking cross-browser compatibility, I found out that the theme broke on Google Chrome, which, led me to spiral down several fixes and customisations to an otherwise very satisfying theme.

My experience with cross-browser compatibility always stated that it's undoubtedly some Javascript that is messing up the images from rendering. After some hacking around, I seem to have found the culprit. Under the "_include" folder (the folder that contains snippings that are stitched together at runtime to render one's page) consisted of a footer.html, for including all Javascript which the page uses. To my surprise, it contained the following code:

<pre><code class="html">
{% raw %}
&lt;script src="{{ '/assets/jquery-2.1.1...."&gt;&lt;/script&gt;
&lt;script src="{{ '/assets/viewportchecker.js..."&gt;&lt;/script&gt;
{% endraw %}
</code></pre>

Well, that's a problem, which, would only mean that I have a blog which would NEVER update jquery and it's corresponding libraries. Plus, since this would be a disk read, it would be slower than a CDN. Time to change all these links to refer to a CDN rather than local files!

<pre><code class="html">
{% raw %}
&lt;script src="https://code.jquery.com/..."&gt;&lt;/script&gt;
&lt;script src="https://cdnjs.cloudflare.com/..."&gt;&lt;/script&gt;
{% endraw %}
</code></pre>

Thankfully, that ended up repairing the theme, and I did not have to do much hacking within viewport.js to get things running for chrome. However, this got me interested in googling more and making the theme more to my liking.

<hr>
## **A New Navigation System**
<hr>
{% include media-image.html folder=images_folder file="a_new_navigation_system-selecting_a_blogging_platform_ii.jpg" title="Changing the Navigation" caption="Adding a search instead of a menu" %}
Out of the box, the navigation menu seemed to be lovely and workable, but not designed for a blog, because a blog would have several posts, and in the end, it would pollute the Menu making it bloated, and this had to change. I pondered hard on what could be the best solution for acing this problem, and in the end, thought that a search-style navigation would be the best fit. A lot of what one wants to go through is available on the home screen, but if the volume increases exponentially and someone needs to go to an article that she or he remembers vaguely, can utilise the search bar, which meant that the search had to be pristine.


After searching for quite some time, I came across [Algolia](https://community.algolia.com/jekyll-algolia/) and [Lunr.js](https://learn.cloudcannon.com/jekyll/jekyll-search-using-lunr-js/). The former is how I wanted my search to be, that is, asynchronous. However, this does limit me to the number of indexing operations per month, but they happen to have amicable plans for anything open-source. I intended my blog to be under CC 1.0 and have a reasonably liberal license, which would not be a hindrance in the rare chance that my blog blows up. To integrate Jekyll with Algolia, I had to modify the "_config.yml" file to include Algolia's gems.

<script src="https://cdnjs.cloudflare.com/ajax/libs/highlight.js/9.15.6/languages/yaml.min.js"></script>
<pre><code class="yaml">
# Gems
plugins:
  - jekyll-paginate
  - jekyll-feed
  - jekyll-algolia

# algolia
algolia:
  application_id: DDFRKSHRJD
  index_name:     bytesapart
  search_only_api_key: c68086dcf7e5c2f0a8b334dcd77252e9
</code></pre>

For the generation of the Algolia's ApplicationID and Search API Key, one needs to register at [Algolia](https://www.algolia.com/). Post that; there is some indexing that needs completion on one's Jekyll blog, by executing the following command:
<pre><code class="plaintext">ALGOLIA_API_KEY='your_admin_api_key' bundle exec jekyll algolia</code></pre>
Algolia's [Documentation](https://community.algolia.com/jekyll-algolia/getting-started.html) does an excellent job in showcasing how one can integrate Algolia with Jekyll.

The Algolia integration also meant that the frontend needed some changes, which is by changing the styling slightly to expand the white background of the Menu and inject a search bar within that space, and inclusion of Algolia's instantsearch.js within the search menu.

<pre><code class="html">
&lt;!-- Algolia --&gt;
&lt;link rel="stylesheet" type="text/css" href="https://cdn.jsdelivr.net/npm/instantsearch.js@3.0.0/dist/instantsearch.min.css"&gt;
&lt;link rel="stylesheet" type="text/css" href="https://cdn.jsdelivr.net/npm/instantsearch.js@2.10.4/dist/instantsearch-theme-algolia.min.css"&gt;
</code></pre>

<hr>
## **Few Minor Tweaks**
<hr>
{% include media-image.html folder=images_folder file="minor_tweaks-selecting_a_blogging_platform_ii.jpg" title="Tweaking styles" caption="Adding and editing some css and js" %}
I intended to use [animate.css](https://daneden.github.io/animate.css/) for all animations (with a little over the top ones), which also meant that I need to load the entire page first and then display it; otherwise, a quick scroll ruins the animation. Therefore, I had to opt for a page-loader, and here, I did not want to use a GIF. A quick google leads me to this [codepen](https://codepen.io/danielmorosan/pen/XmYBVx) page. I did change it slightly to my liking but used it overall as-is.

For all the code snippets, I prefer using [Fira Code](https://github.com/tonsky/FiraCode) as my font, since that is what I use in my IDE, along with a Dark Theme. The theme did come with a good code snipping highlighting tool, though I prefer using highlight.js since it has a plethora of syntax highlighting for many languages.

Also, I needed something where I could host this Jekyll site, and make the builds automated, rather than building it manually and deploying to some old-school CPanel based server. My options were [GitHub Pages](https://pages.github.com) and [GitLab Pages](https://about.gitlab.com/product/pages/) out of which, at the time of when I was bringing up this blog, GitHub did not offer a custom gem build (which is odd, since Jekyll is a brainchild of GitHub). I ended up going with GitLab Pages, since the instructions were crystal clear, and that there was the support of custom gems which this theme has, and I may need some in the future. All this meant setting up a ".gitlab-ci.yml" file for trigging the Continous Integration build.

<pre><code language="yaml">
pages:
  stage: deploy
  script:
  - gem install jekyll
  - bundle exec jekyll build -d public
  artifacts:
    paths:
    - public
  only:
  - master
</code></pre>

There were also some other minor tweaks such as changing the path to the images folder to have a subfolder per post rather than treat the "images" folder as a dumping ground, and the addition of a 404.html page, rather than let the default GitLab Pages handle it. Some other changes involved adjusting some small margins, the addition of a horizontal line at the beginning of every section, and complete transparency of post images on hover. Overall these tweaks were minor and subtly changed the aesthetics but add to the overall ambience of the blog.

In conclusion of the series, I believe choosing Jekyll was a right choice since getting up-and-running with it seemed very simple and did not feel as bloated as WordPress, even though the later is known the territory. A few changes were necessary to make the blog suite my needs, but those tweaks did not mean heading into convoluted PHP and hitting one's head against the wall dealing with WordPress's convoluted structure. Even though these first two posts are not something that offers much depth into programming or on diving deep into the changes, I do tend to take this blog in a more depth-first approach for future posts. Let's say I needed to pull out of web-dev and needed some posts to get out in the time I thought about the direction of taking this blog.