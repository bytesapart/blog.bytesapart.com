---

layout: default
title: Selecting a Blogging Platform
type: post
navigation: false

date:   		2018-04-22 00:12:05
excerpt: 		In the quest of starting a blog, I faced numerous choices of blogging platforms.
            Here's my experience with them, and why I ended up choosing what I chose.
categories:		programming
gradient: 		2
image: 			selecting_a_blogging_platform.jpg
details:		false
permalink: "/selecting-a-blogging-platform/"

author: 		Osama Iqbal
bio: 			Data is always in a state of quantum superposition unless observed upon by visualisations.
twitter: 		"http://twitter.com/bytesapart"
linkedin: 		"https://www.linkedin.com/in/osamaiqbal/"
rss: 			"https://www.bytesapart.com/feed.xml"

---

For the past year, in my spare time, I've always tried to start a blog that would end up being a detailed repository of whatever
I've learnt or whatever I'll be learning. The most challenging part of this happens to be selecting a blogging platform that gives
you the flexibility to edit, and offers a good user experience to those that visit the website.  

<hr>
## **The Checklist**
<hr>
{% include media-image.html file="checklist-selecting_a_blogging_platform.jpg" title="Checklist" caption="A checklist of desired features helped in narrowing down the hunt" %}
Out of the plethora of blogging platforms available, I needed something which satisfied certain criteria. This 'checklist' acted like
a filter which helped me narrow down to my solution. I did not treat this list as a hardcoded requirement that I must adhere to, but
something that adds points towards what I desire from the platform. The list happens to be
- **Must be customisable:** This was something of a priority. As a programmer, I needed a hackable medium which I could get into any time and tweak
if I didn't like a particular feature, or if I wanted to add a new feature.
- **Documentation:** A good documentation to assist with the intricacies of the API was necessary. Without good documentation, one ends up spending
more initial effort in understanding the way things assembled and how they work, which leads to less blogging and more web development, at which I
happened not to be good.
- **Available Themes:** The previous point and this one are somewhat connected. In order to save time in doing more stuff, rather than being a part anytime
web developer, I needed a blogging framework that not only had support for custom themes, but there was also a community at large that was involved in building
custom themes, be it paid or free (as in free beer). That would allow me to use the base theme, read the documentation and customise accordingly.
- **Lightweight, easily hostable:** I needed the platform to be lightweight, which means that it didn't bog me down with unnecessary features which I'll probably
never end up using, but sound perfect on paper. Another desirable attribute was the ability to host the blog easily, which need not be inherently in-built within
the blogging framework, but custom Docker images which would make life easier were always welcome.

<hr>
## **The Wordpress Addiction**
<hr>
{% include media-image.html file="wordpress-selecting_a_blogging_platform.jpg" title="Wordpress" caption="The undisputed king" %}
Wordpress happened to be an almost natural choice, given the fact that while I was in university, I used to make a ton of
Wordpress websites for clients, which involved integrating WooCommerce, Visual Composer and other famous plugins for added functionality.
Wordpress happens to be this batteries-included, all-inclusive powerhouse. Its customisability is far ahead of all other blogging platforms.
Since WordPress happens to be one of the oldest CMS (Content Management System) out there, one can find a plugin for almost anything.
Which means that this was both customisable and that it had extensive documentation that led to a thriving community. A larger community in turn
indicated more themes available on a variety of marketplaces.

The only glaring problem was that it required a server to host, which could have been done with the help of shared hosting or with a cloud server, through
the server route always seemed more pleasant to go, since you get all the control at the cost of additional maintenance charges. There are some excellent guides
on how to host a Wordpress website on a cloud service, such as the one by [DigitalOcean](https://www.digitalocean.com/community/tutorials/how-to-install-wordpress-with-lamp-on-ubuntu-16-04).
One thing which I wasn't very fond of when it came to Wordpress was the fact that I needed a Database that will contain all my posts and all the security loopholes that come along with Databases. When you want something that is minimalistic, databases are a big no-no.

Blog themes tend to be geared more towards magazine publications, or towards multi-user theme oriented blogs. I was neither. Luckily, I had a great theme lying around,
called [Astro](https://themeforest.net/item/astro-responsive-wordpress-blog-theme/7128412). It had the exact minimal look which I desired, so I quickly fired it up on
a [Vultr](https://www.vultr.com/)  VPS (Virtual Private Server). To get things useful in WordPress, there are a ton of plugins that one needs to install, such as [Jetpack](https://jetpack.com/), [Yoast SEO](https://yoast.com/wordpress/plugins/seo/), [Wordfence](https://wordpress.org/plugins/wordfence/), etc, which adds to the already massive installation consisting of a
database making it feels clunky already.

The user-friendly approach always gets to me, because of the emphasis on visual design and the use of shortcodes for achieving small things. I'm the kind of person
that feels at home in a text editor, rather than some WYSIWYG web-based editor with an added text option. As much as the customizer is helpful in getting a live
preview of what changes you make, I always felt restricted by it. I could potentially get inside the functions.php file and the like and edit to my heart's content,
which I did end up doing for a couple of days, only to realise that this isn't as easy to hack quickly at, like plain old HTML. After wasting a week or so become a part-time
Wordpress developer, I knew there has to be some other way. Portability from [Vultr](https://www.vultr.com/) to [DigitalOcean](https://www.digitalocean.com/) was also something
that I had kept in mind, therefore, setting up [Docker](https://www.docker.com/) along with [Docker Compose](https://docs.docker.com/compose/) took some time (I don't happen to be an Infra guy, but can get my head around it provided I put time into it). Not-so-easy-and-slow modifications, a Database with security issues, multiple plugins to get it up and running along with
hosting costs which I could never recover since it was meant to be more of a personal project, suggested that I had to keep Wordpress as Plan-B and search for some other platform out there.

<hr>
## **Fishing with Pelican**
<hr>
{% include media-image.html file="fishing-with-pelican-selecting_a_blogging_platform.jpg" title="Pelican" caption="A pythonic static generator" %}
My forte happens to be the Python programming language. Even though I boast about being a polyglot, there are only a couple of languages that I know
of very well due to ages of practising. My full-time Job also happens to be heavy on Python, so it was only natural that I searched for a platform
that used python. [Pelican](https://blog.getpelican.com/) happens to be a perfect fit for this. It's a static site generator, which means that
we have gotten rid of the Database, removing any security issues that come with Databases, along with removing a Framework, such as Wordpress, which
has it's own [CVE](https://cve.mitre.org/cgi-bin/cvekey.cgi?keyword=wordpress) issues.

A static site generator happens to sit somewhere in between plain text and HTML. Every blog has reusable content. If I were writing my blog in plain
HTML, this would mean copying and pasting large chunks of HTML code over for each post, and changing only the content part of it for every page.
Static site generators help you to write your blog in Markdown (something which is next to plain text) and compile the content which you have
written along with the HTML to generate pages on the fly. This way, your final user is consuming plain HTML, while you could potentially employ a
CI (Continuous Integration) to keep building your site on every code commit to a particular Version Control Software's branch, which works amazingly well,
as the HTML can be cooked up by a single person, with a little bit of template code specific to every static site generator.

Pelican, a static site generator, had the above pluses. Adding to that, it had a sizeable community and used Jinja Templating, which was somewhat
in familiar territory, and it's written in python. Which meant the installation would be more comfortable and if things go south, and that there would be fewer chances of
me shying out to dive deeper into the code to fix the problem, rather than finding an alternate around it. The only problem that I had with Pelican was
that it didn't have good templates. The theming community seemed not to be interested in releasing commercial themes which could be purchased but have
a higher degree of quality over their open-source parts. There was this one particular theme which I liked, called as [Attila](https://github.com/arulrajnet/attila/),
which happened to be a port of a Ghost Theme (Lightweight Wordpress, in my opinion).

I did like the theme, but I didn't love it. After spending some time with Pelican trying to learn and modify the theme, I realised that I'd have to do a ton
of web development to give it the quality I require and not make it feel like a generic off-the-shelf theme. That again proved to be hectic due to the time constraint which I had, though I got to learn a lot about static site generators from there. What killed my decision to use Pelican and for that matter
even [Hugo](https://gohugo.io/) was the fact that there were themes, some outstanding ones too, but none that fit my taste, and none with that premium feel to it, which I
could potentially purchase if I felt like it.

<hr>
## **Dr. Jekyll**
<hr>
{% include media-image.html file="jekyll_logo-selecting_a_blogging_platform.png" title="Jekyll" caption="Static site generation behemoth.<br />Image Credits: <strong><a href='https://github.com/jekyll/brand' style='color: #eb2344;text-decoration: none;'>Jekyll Brand</a>.</strong><br /> Image License: <strong><a href='https://github.com/jekyll/brand/blob/master/LICENSE' style='color: #eb2344;text-decoration: none;'>CC-BY-4.0</a>.</strong>"%}
After picking up Pelican for some time, I looked into other Static Site Generators, though not from a coding or API perspective. I looked at them from a 'Users' perspective to decide whether
the criteria of premium themes was fitting perfectly. Out of all the generators, Jekyll stood out. Jekyll seemed to be one of the oldest generators out there, with a thriving
community, loads of tutorials for it, along with a bunch of premium themes, along with free ones that had a premium feel to it. Two themes that caught my attention were
[Minimal Mistakes](https://mmistakes.github.io/minimal-mistakes/) and [Hashtag](https://themeforest.net/item/hashtag-for-jekyll-an-elegant-blog-theme/7721454). I loved them both. The former was free of cost, while the latter being premium. I came across the former theme through a [blog post](https://mtlynch.io/why-i-quit-google/) which went viral on Reddit.
The premium theme was somewhat old and had not been updated, breaking on chrome. I did like it's out-of-the-box animations and colour schemes while maintaining a minimalistic look.
Either way, I had to modify both the themes to a degree to my liking. I decided to go with the premium theme even though it had browser compatibility as I wouldn't have to deal
with much JQuery/Javascript, something which I was trying to avoid actively. The free theme was loaded with SEO options and optimised very, very well because of which delayed my decision to go with the premium theme.

Jekyll gave me all the perks which were available in other generators, with the added benefit of being stable due to its age and the fact that it had extensive step-by-step documentation, along with the fact that there was an option of premium themes which looked good. In the end, I hacked away a little bit at both the themes, only to realise that the premium one had some decent SEO related modifications. I decided to stick with the premium one. In my next blog post, I'll cover what adjustments went into the theme, and the frustration of returning to the world of web development after a very long time.
