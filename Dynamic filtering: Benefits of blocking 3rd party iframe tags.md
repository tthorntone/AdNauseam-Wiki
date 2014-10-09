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

The title is obviously an exaggeration (the tracking _can_ be blocked).

The particular `addthis.com` javascript code which attempts to fingerprint your browser executes from within a 3rd-party `iframe`.

Contrary to what Adblock Plus has been claiming on [its blog](https://adblockplus.org/blog/adblock-plus-and-the-canvas-fingerprinting-threat) and the [media](http://news.yahoo.com/adblock-plus-stop-canvas-fingerprinting-unstoppable-browser-tracking-191541979.html), using _EasyPrivacy_ does **not** prevent AddThis from fingerprinting your browser. This is something I verified and re-verified back then, and I just re-verified again (2014-10-09):

When you visit <http://www.ibtimes.com/>, the following `<iframe>` is dynamically created:

    <iframe id="_atssh478" title="AddThis utility frame" src="//ct1.addthis.com/static/r07/sh175.html#iit=1412897324950&amp;tmr=load%3D1412897319899%26core%3D1412897320635%26main%3D1412897324941%26ifr%3D1412897324955&amp;cb=0&amp;cdn=1&amp;chr=UTF-8&amp;kw=headline%20news%2Cdaily%20news%2Cbreaking%20news%2Cbusiness%20news%2Cpolitical%20news%2Csports%20news%2Ccurrent%20news%2Ceurope%20news%2Cworld%20news%2Casian%20news%2Ccomputer%20news%2Cairline%20news%2Cbanking%20news%2Cconsumer%20news%2Chealth%20news&amp;ab=-&amp;dh=www.ibtimes.com&amp;dr=&amp;du=http%3A%2F%2Fwww.ibtimes.com%2F&amp;dt=International%20Business%20Times%20-%20International%20Business%20News%2C%20Financial%20News%2C%20Market%20News%2C%20Politics%2C%20Forex%2C%20Commodities&amp;dbg=0&amp;md=0&amp;cap=tc%3D0%26ab%3D0&amp;inst=1&amp;vcl=1&amp;jsl=143585&amp;prod=undefined&amp;lng=en-GB&amp;ogt=title&amp;pc=flw%2Ctbx&amp;pub=ra-4fd117ff2700b0d1&amp;ssl=0&amp;sid=54371a28bc1109db&amp;srpl=1&amp;srcs=1&amp;srd=1&amp;srf=1&amp;srx=1&amp;ver=300&amp;xck=0&amp;xtr=0&amp;og=title%3DAmerican%2520Horror%2520Story&amp;aa=0&amp;csi=undefined&amp;rev=6.2&amp;ct=1&amp;xld=1&amp;xd=1" style="height: 1px; width: 1px; position: absolute; z-index: 100000; border: 0px; left: 0px; top: 0px;"></iframe>

And within it, the fingerprinting will take place, and result reported to AddThis servers:

- **Request URL:** `http://ct1.addthis.com/static/r07/sh175.html`
- **Cookie:** `uid=54371180c23c9d63; __atuvc=1%7C41; uit=1; km_ai=543717496fd011.83307994`
- **Host:** `ct1.addthis.com`
- **Referer:** `http://www.ibtimes.com/`

The above occurred with Adblock Plus with _EasyList_ + _EasyPrivacy_ enabled. Note that the cookie header which contains the fingerprinting information will be stripped if you set your browser to block 3rd-party cookies and site data.

AddThis and many other 3rd-parties which purpose is to data-mine you will be foiled by blocking 3rd-party `<iframe>` tags (even more so if blocking 3rd-party `<script>` tags).

By blocking 3rd-party `<iframe>` tags, you don't have to [ask them permission to opt-out](http://www.addthis.com/privacy/opt-out) of something you did not opt-in in the first place. ("Opting out" is a joke anyways, [see _"The web never forgets"_ (PDF)](https://securehomes.esat.kuleuven.be/~gacar/persistent/the_web_never_forgets.pdf), section 6.2)