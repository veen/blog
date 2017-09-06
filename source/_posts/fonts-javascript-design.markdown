---
layout: post
title: "Fonts, JavaScript, and How Designers Design"
date: 2009-06-02
author: Jeffrey Veen
featured: true
---
The W3C recommendation for <a href="http://www.w3.org/TR/css3-webfonts/">CSS web fonts</a> will be 7 years old soon. Why, after all these years, has typography for the web not progressed further? Why haven&#8217;t designers embraced linked, downloadable fonts in their designs?

We&#8217;ve spent a lot of time thinking about this as we&#8217;ve been planning and building Typekit. It certainly feels like things are different now &#8211; browsers are developing <a href="http://openfontlibrary.org/wiki/Web_font_linking_with_@font-face?ccm=/wiki/Web_font_linking_with_@font-face">font support</a> in open and interoperable ways; <a href="http://gigaom.com/2009/05/27/700-million-broadband-subscribers-by-2013/">bandwidth has increased</a> to allow for additional page elements. But perhaps most importantly, designers can start using fonts in their designs without having to change the way they work.

## Tools for native web designers

We&#8217;ve been talking to a lot of designers — from hobbyists to some of the top professionals on the web — and we consistently hear them talk about their workflow. Very few designers these days use a <a href="http://www.microsoft.com/expression/">unified suite of tools</a>. Rather, they pull together what works, and spend the majority of their time writing markup by hand.

Any solution that hopes to bring rich typography to the web will need to accommodate multiple ways of working with the technology. When we thought about how Typekit could support all the ways designers and developers work, we started developing a number of features that would be valuable <em>in addition</em> to having access to fonts.

## More control

Our goal from the very beginning has been to provide high quality fonts through a ridiculously easy to use service. That&#8217;s one of the reasons we use Javascript. By adding a line of code in your site&#8217;s pages, you&#8217;ll be able to use the Typekit site to control the following:

* Automatic CSS declarations. Once the code is in your page, you simply chose a font and decide what selectors to use. Reload and the font shows up. You don&#8217;t even need to edit your markup.

* Dynamic kerning and ligature control. Modern browsers are doing a great job at supporting @font-face linking, but it&#8217;s early yet. OpenType fonts have loads of capabilities and features like ligatures, kerning pairs, tabular numerals, and more. How all browsers on all platforms support those features varies, but we&#8217;ve been using Javascript to smooth some of that out.

* Fonts are loaded and rendered. Standards-based implementations also vary in the actual experience users have with the browsers. For example, how should pages reflow after the fonts are downloaded? What should happen while they&#8217;re downloading? Answers to these questions should be up to the site designer.

* Support for older browsers with fallbacks like <a href="http://wiki.github.com/sorccu/cufon/about">Cufón</a>, <a href="http://wiki.novemberborn.net/sifr3/">sIFR</a>, or other techniques. For years now, clever designers and developers have created innovative workarounds to the lack of font support on the web. By using Javascript, we can offer selective support for these technologies.

## Nuts and bolts
Sometimes we use automatic services and are happy they just work. Other times, we want to see behind the scenes and have as much control as possible. For some developers, every semi-colon and bit of whitespace is considered and checked. Adding linked fonts to your site shouldn&#8217;t affect this.

If, as a web designer or developer, you may want the option to simply hand-code your site, or have your markup and style programatically generated via a CMS. There are two ways you&#8217;ll be able to do this:

* Javascript API. If you&#8217;re comfortable writing script to control your pages, we&#8217;ll have an API you can use to define what selectors use each font. This gives you access to many of the features described above, but without having to incorporate the the Typekit web app into your workflow.

* CSS linking. If you really want direct access to fonts, then simply link to a hosted CSS file containing the `@font-face` definitions. You&#8217;ll have to forgo all of the additional features, but you&#8217;ll be as close to the fonts as you can be. Why not just give links to the font files directly? Because we believe that automatically serving EOT files for Internet Explorer is a core service we can provide. But we&#8217;re open to discussing even this. Let us know in the comments.

In either of these cases, you&#8217;ll be able to write CSS stacks using font names you get from Typekit.

## Making it go

Our goal is to support designers and developers with tools that make it easier and more efficient to practice their craft. How will typography fit in? It may be too early to tell. A few years back, the shift from largely static pages to an Ajax-enabled web coincided with a commitment to building sites with web standards. This resulted in new tools, new skills, and new methods for doing our work. Adding great typography will only take us farther. We hope to be a part of this evolution.
