---
layout: post
title: "Serving and Protecting Fonts on the Web"
date: 2009-07-21
author: Jeffrey Veen
---
When describing Typekit to both web and type designers, we often say that we&#8217;re &#8220;offering a level of protection that the type industry needs.&#8221; Considering all the discussion there has been recently about differing formats and safeguarding fonts, we thought we&#8217;d explain our approach in detail.

The fact is, for something to appear in a browser, it has to be on the web. If it&#8217;s on the web, it can&#8217;t be completely protected. Recent history has shown repeatedly that attempts to manage digital rights through code have been <a href="http://news.bbc.co.uk/2/hi/technology/7813527.stm">rejected by consumers</a> and <a href="http://www.ftc.gov/opa/2007/01/sony.shtm">drawn legal fire</a>.

While the entertainment industry has wrestled with this issue for a decade, it&#8217;s only recently became a concern for foundries and type designers. Browser release schedules don&#8217;t iterate as fast as opinions do, and that requires everyone to experiment in public. Can commercial fonts be used in a way that doesn&#8217;t turn every website into a free font server? With Typekit, we feel there&#8217;s an opportunity to find a middle ground.

## Depth in Defense

<a href="http://en.wikipedia.org/wiki/Defense_in_depth">Defense in depth</a> is an old military strategy and an apt analogy for what we&#8217;re doing. Armies would put barrier after barrier between them and the enemy. Each trench or string of barbed wire was relatively easy to get past, but each one slowed them down and tired them out a little. Dozens and dozens of these small hurdles would eventually wear them down.
We&#8217;ve put up a few hurdles of our own. Our intent is only to <em>discourage casual misuse</em> and to make it clear that taking fonts from Typekit is an <em>explicit and intentional act</em>.  Here&#8217;s what we&#8217;re doing.

## Levels of Protection

* **HTTP referrer checking** Only authorized domains are allowed to link to fonts. If you take the URL for our CSS or fonts and try to link them to your site — or just try to load them directly in your browser  — you&#8217;ll get no response. To circumvent this, you&#8217;ll need to use curl or some other command line http user agent to spoof the referrer. But this technique helps us protect the service from <a href="http://en.wikipedia.org/wiki/Hotlinking">Hotlinking</a> and helps prevent quick &#8220;grab the link and try it on my site&#8221; experimenting.</li>
<a href="https://typekit.files.wordpress.com/2009/07/data-url1.png"><img style="float:right;margin-left:10px;border:1px solid silver;" src="https://typekit.files.wordpress.com/2009/07/data-url1.png?w=262&#038;h=215" alt="Fonts as Data URIs in Firebug" width="262" height="215" /></a>

* **Obfuscation** Hard-to-guess file names are not security. Not even a little bit. But files listed as strings of seemingly random characters can be intimidating to those who aren&#8217;t familiar with the conventions of viewing source or launching tools like Safari&#8217;s Activity Window or Firefox&#8217;s Firebug. To that end, our Javascript is minified and the fonts themselves are represented as Base64 encoded strings. You may see right through this, but the vast majority of web users wouldn&#8217;t know what to make of it.</li>

* **Data URIs** We don&#8217;t just encode the fonts to make them look scary. We do this so they can be injected in-line with our generated CSS. While this adds about 20 percent to the file size, it&#8217;s actually more performant because we eliminate all but one HTTP connection. According to the Yahoo Developer <a href="http://developer.yahoo.com/performance/rules.html#num_http">best practices</a>, &#8220;Most time is tied up in downloading all the components in the page: images, stylesheets, scripts, Flash, etc. Reducing the number of components in turn reduces the number of HTTP requests required to render the page. This is the key to faster pages.&#8221;</li>

* **Visible license data** Based on the proposed metadata of the .webfont initiative, we&#8217;ve included license, copyright, and &#8220;allowed&#8221; domains as comments in our CSS. While the browser doesn&#8217;t currently support an automated mechanism for approving or displaying those rules, they are still a visible reminder that repurposing the files is illegal. Removing this text is easy, but it&#8217;s another explicit act.</li>

* <a href="https://typekit.files.wordpress.com/2009/07/segmented-font.png"><img class="alignright" style="float:right;margin-left:10px;border:1px solid silver;" src="https://typekit.files.wordpress.com/2009/07/segmented-font.png?w=166&#038;h=114" alt="Segmented font in Mac OS X" width="166" height="114" /></a> **Segmenting and subsetting** Even if you follow these steps, the resulting font files won&#8217;t contain the full character set. We split requested fonts into multiple files and recombine them using the CSS font stack. And we are subsetting only character sets requested by the Typekit user to improve performance. To make a usable and installable font, you&#8217;ll need to open a font authoring tool and recombine the glyphs.</li>

With enough knowledge of web technologies, it&#8217;s possible to circumvent each one of these steps. Many can be automated with scripts and command line tools. In aggregate, they provide enough of a barrier to discourage all but the most motivated. And as we&#8217;ve seen over and over again, <a href="http://en.wikipedia.org/wiki/Jon_Lech_Johansen">those with enough time and talent</a> will find ways around any attempt at security. The reality is that there are countless places that make it far easier to steal fonts, if that&#8217;s your goal.
Our goal is different. After talking to dozens of foundries, we&#8217;ve found traction with a solution that works today and moves the conversation forward. With it, we hope to provide the easiest place to use real fonts on the web, legally and licensed, and to compensate type designers for their amazing contribution to visual communication.

_You can see this all in action on one of the sites sites participating in our technology preview: <a href="http://forabeautifulweb.com/">For A Beautiful Web</a>._
