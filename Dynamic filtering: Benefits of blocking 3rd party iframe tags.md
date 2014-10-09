<p align="center"><img src="https://raw.githubusercontent.com/gorhill/uBlock/master/doc/img/dynamic-filtering-7.png" /><br><sup>3rd-party &lt;iframe&gt; tags blocked by default for all sites.</sup></p>

### Malware protection

URL: <http://www.riskiq.com/resources/blog/jquerycom-malware-attack-puts-privileged-enterprise-it-accounts-risk>

`iframe` are very often used by malware code on compromised web sites. The most recent example of this is [jquery.com](http://blog.jquery.com/2014/09/24/update-on-jquery-com-compromises/).

The web site was compromised, and users of the site were served tainted web pages, which were causing a user's browser to download exploit kit from some remote servers. This was done first through a malicious 3rd-party `<script>`, which purpose was to dynamically create and embed a 3rd-party-sourced `<iframe>` on the page.

Using 3rd-party-sourced `<iframe>` to inject exploit on a user's computer is quite a common technique. [Example](http://arstechnica.com/security/2013/10/hackers-compromise-official-php-website-infect-visitors-with-malware/), [example](http://www.wired.com/2013/08/freedom-hosting/), [example](http://blog.armorize.com/2011/07/willysycom-mass-injection-ongoing.html), etc.

Simply blocking 3rd-party `<iframe>` by default foils such exploit.

In the above case, blocking 3rd-party scripts would have been even better, as the malicious code would have been prevented from creating the malicious `<iframe>` in the first place. But for users with low tolerance to site breakage, blocking 3rd-party `<iframe>` by default (i.e. on all sites by default) is really the best solution.

Ultimately, if a site breaks because it really does need legitimate 3rd-party `<iframe>`, then un-blocking `<iframe>` for a specific site is only one click away:

<p align="center"><img src="https://raw.githubusercontent.com/gorhill/uBlock/master/doc/img/dynamic-filtering-8.png" /><br><sup>3rd-party &lt;iframe&gt; tags blocked by default for all sites,<br><b>except</b> for the current site (this was for github.com).</sup></p>

### Tracking protection

URL: <http://www.propublica.org/article/meet-the-online-tracking-device-that-is-virtually-impossible-to-block>

Remember the article [ProPublica's _"Meet the Online Tracking Device That is Virtually Impossible to Block"_](http://www.propublica.org/article/meet-the-online-tracking-device-that-is-virtually-impossible-to-block)?

The title is obviously an exaggeration (the tracking _can_ be blocked), but the particular `addthis.com` javascript code which attempts to fingerprint your browser executes from within a 3rd-party `iframe`. Contrary to what Adblock Plus has been claiming on its blog and the media, using _EasyPrivacy_ does **not** prevent AddThis from fingerprinting your browser. This is something I verified and re-verified back then, and unless appropriate filters have been added since last time I checked, it still is the case.

AddThis and countless other 3rd-party which purpose is to data-mine you will be foiled by blocking 3rd-party `<iframe>` tags (even more so if blocking 3rd-party `<script>` tags).