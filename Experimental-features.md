This page is about the experimental features which you can enable in µBlock. Features which I think are good for the users but which I consider aren't yet mature in design/implementation are considered experimental.

Experimental features are disabled by default, you can enabled them in the _Settings_ tab in the dashboard. As long as a feature is labeled "experimental", I can't guarantee it will work flawlessly.

If something doesn't work as expected, I suggest you first disable _"Experimental features"_ in the dashboard then see if the problem persist.

### Privacy exposure reduction: local mirroring

One way users increase their privacy exposure is through [content delivery networks](http://en.wikipedia.org/wiki/Content_delivery_network) ("CDN") and likes. Good examples of CDN are `ajax.googleapis.com`, `cdnjs.cloudflare.com`, `googletagservices.com`, etc. These servers are used to serve resources to countless web sites.

When a resources is pulled from one of these CDNs, typically the [referrer header](http://en.wikipedia.org/wiki/HTTP_referer) is set in the HTTP request, which allows ubiquitous CDNs to collect data about your browsing habits. Not good for privacy.

In the spirit of reducing privacy exposure, local mirroring is introduced as an experimental feature in µBlock. Local mirroring allows µBlock to cache locally resources pulled from known ubiquitous CDN, and future requests for the same resource will be served locally rather than pulling it from the CDN: not pulling a resource from a CDN prevents that CDN from collecting data about your browsing habit.

![zdnet.com](https://raw.githubusercontent.com/gorhill/uBlock/master/doc/img/local-mirroring-example-1.png)

The picture above shows that connections to `ajax.googleapis.com`, `www.googletagservices.com`, `twitter.com` were prevented -- hence no trace left in their server logs), and local copies of the requested resources were served instead -- hence no page breakage. (Surprisingly, the above shows that requests to `googletagservices.com` are [**not blocked**](https://hg.adblockplus.org/easylist/rev/9f6e928c258a) when using _EasyList_ + _EasyPrivacy_. (_"Dan Pollock's"_, _MVPS_ and _hpHosts_ block it though.)

A quick benchmark -- using [reference benchmark](https://github.com/gorhill/uBlock/wiki/%C2%B5Block-and-others:-Blocking-ads,-trackers,-malwares), with the feature disabled vs. enabled shows the following:

**Disabled:** <br>
URLs visited: 60 <br>
**Domains: 415** / 475 <br>
Scripts: 857 / 1264 <br>
Outbound cookies: 0 / 130 <br>
Net requests: 3,304 / 6,264 <br>

**Enabled:** <br>
URLs visited: 60 <br>
**Domains: 337** / 397 <br>
Scripts: 793 / 1214 <br>
Outbound cookies: 0 / 132 <br>
Net requests: 3,174 / 6,156 <br>

As seen above, a significant amount of connections to third-party ubiquitous CDNs were foiled with local mirroring enabled. This contribute to reducing privacy exposure, without breaking web pages.

![Local mirroring results](https://raw.githubusercontent.com/gorhill/uBlock/master/doc/img/local-mirroring.png)

Advantages of local mirroring:
- Reduction of privacy exposure
- Less bandwidth
- Faster page load

Disadvantage of local mirroring:
- Higher memory consumption

##### Update

[Following cut & pasted [from here](https://github.com/gorhill/uBlock/issues/264#issuecomment-57812998)]

I ran a new benchmark with uBlock 0.6.6.0-rc.0 and ABP 1.8.5 with the same lists (except Peter Lowe's because there is no easy convenient way to install it in Adblock Plus -- so I assume users are likely to not bother).

Here is the resulting diff: https://www.diffchecker.com/5z91i47m

In red what ABP blocked which was not blocked by uBlock.
In green what uBlock blocked which was not blocked by ABP.

I suspect the only two requests not blocked by uBlock which were blocked by ABP is just the result of the page content changing between the time I benchmarked uBlock and ABP.

Filter lists:
- ABP: Out of box settings + EasyPrivacy, Malware domains, Fanboy's Social Blocking List, Anti-ThirdpartySocial‎ + "Acceptable ads" disabled
- uBlock: Out of box settings + Anti-ThirdpartySocial‎ + Local mirroring enabled and primed (as it would be through normal use).

What local mirroring accomplished in the above benchmark... Prevented connections to:
- `2mdn.net`
- `ajax.googleapis.com`
- `cloudflare.com`
- `fonts.googleapis.com`
- `googletagservices.com`
- `gstatic.com`
- `janrain.com`
- `jquery.com`
- `twitter.com`

And since the remote resources were available locally, preventing the connection didn't cause page breakage.

##### Update 2014-10-10:

I had to remove a couple of hostnames which were candidate to be mirrored, as in practice it showed that these could not be safely mirrored: `2mdn.net`, `googletagservices.com`, `janrain.com`. At this point it does look like the local mirroring feature will really have to be strictly reserved for resources which we know for sure are immutable (libs, fonts, things like that).

##### Update 2014-10-12:

Well there were bugs introduced in 0.7.0.0 re local mirroring. These have been fixed. So I put back `googletagservices.com` as local mirror candidate, as the breakage was most certainly caused by the bugs, not the fact that the resources were not immutable (they appear to be).