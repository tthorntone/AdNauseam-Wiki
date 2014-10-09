<p align="center"><img src="https://raw.githubusercontent.com/gorhill/uBlock/master/doc/img/dynamic-filtering-7.png" /><br><sup>3rd-party &lt;iframe&gt; tags blocked by default for all sites.</sup></p>

### Example 1

URL: <http://www.riskiq.com/resources/blog/jquerycom-malware-attack-puts-privileged-enterprise-it-accounts-risk>

`iframe` are very often used by malware code on compromised web sites. The most recent example of this is [jquery.com](http://blog.jquery.com/2014/09/24/update-on-jquery-com-compromises/).

The web site was compromised, and users of the site were served tainted web pages, which were causing a user's browser to download exploit kit from some remote servers. This was done 1st through a malicious 3rd-party `<script>`, which purpose was to dynamically create and embed a 3rd-party-sourced `<iframe>` on the page.

Using 3rd-party-sourced `<iframe>` to inject exploit on a user's computer is quite a common technique. [Example](http://arstechnica.com/security/2013/10/hackers-compromise-official-php-website-infect-visitors-with-malware/), [example](http://www.wired.com/2013/08/freedom-hosting/), [example](http://blog.armorize.com/2011/07/willysycom-mass-injection-ongoing.html), etc.

Simply blocking 3rd-party `<iframe>` by default foils such exploit.

In the above case, blocking 3rd-party scripts would have been even better, as the malicious code would have been prevented from creating the malicious `<iframe>` in the first place. But for users with low tolerance to site breakage, blocking 3rd-party `<iframe>` by default (i.e. on all sites by default) is really the best solution.

Ultimately, if a site breaks because it really does need legitimate 3rd-party `<iframe>`, then un-blocking `<iframe>` for a specific site is only one click away:

<p align="center"><img src="https://raw.githubusercontent.com/gorhill/uBlock/master/doc/img/dynamic-filtering-8.png" /><br><sup>3rd-party &lt;iframe&gt; tags blocked by default for all sites, <b>except</b> for the current site.</sup></p>