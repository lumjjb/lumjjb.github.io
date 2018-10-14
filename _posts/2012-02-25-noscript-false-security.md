---
layout: post
title: Javascript Blocker 'NoScript' may give you a false sense of security with default settings
---

The purpose of Javascript blockers such as "NoScript" for Firefox help to block javascript from running on untrusted sites. Using these add-ons give us a sense of comfort as we may assume that even if content from a domain serves us an intrusive or malicious javascript payload, we are protected (through the browser filtering out the untrusted domain's Javascript calls).

However, with the default settings of "NoScript", attackers can make use of trusted domains to host and deliver their javascript. Some examples where this is possible are for sites that allow the uploading of files or custom content. This includes sites storage, blogs, hosting and repository sites. i.e. Dropbox, Wordpress, blogspot, etc.

## Proof of Concept (POC)
For this article, I will be using DropBox, a popular file storage site, as an example.

Here, an untrusted domain attacker.com serving a javascript from DropBox. In this scenario, the user is a dropbox account user, and thus, has trusted dropbox.com.

{% include youtubePlayer.html id="Bvuqap4-C0o" %}

## Protective Measures (Edit)
> Thanks to Gorgio for highlighting this

To prevent against such implementations of iframes, you may change the default settings under `NoScript Options|Embedded` and check the relevant `Forbid …` options.

If you have any insights into this, your findings and views are greatly welcome! :)

> **Note: The vulnerability and the versions of firefox and NoScript used are the most updated as of the time of this article (25/02/2012). 
