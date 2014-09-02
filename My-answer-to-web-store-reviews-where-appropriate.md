I can't answer to the review in web stores. It's unfortunate as sometimes I could help fix the problem(s), or correct inaccuracies, but the review area is not a forum, so I understand the limitations. Still, I will answer here to those reviews for which I have something meaningful to say.

***

#### Paul Kelly (Chrome store, 2 September 2014)

> This is a very good blocker that needs refinement. It blocks too many non-ad fields, such as blanks to enter passwords and usernames. This app could be the best with tweaks, but AdBlock Plus remains the reference standard. [4-star rating]

µBlock enforces Adblock Plus's _EasyList_ and _EasyPrivacy_, so if µBlock blocks more stuff than Adblock Plus with the **same filter lists** (_EasyList_ + _EasyPrivacy_, as per [EFF's advice](https://www.eff.org/deeplinks/2012/04/4-simple-changes-protect-your-privacy-online)), then this is a bug and it should be reported with appropriate details so that I can reproduce and investigate it. I can't fix things which I am not aware are broken.

***

#### _Review removed_ (Chrome store, 1 September 2014)

> При запуске в коде страницы появляется вставка на какой то сайт hxxp://www.faceporn.net/free `<style id="ublock-preload-1ae7a5f130fc79b4fdb8a4272d9426b5">[href^="http://www.faceporn.net/free?"]
{display:none !important;}</style>` [1-star rating]

Google translate:

> When you run the code page appears insert on what that's hxxp://www.faceporn.net/free `<style id="ublock-preload-1ae7a5f130fc79b4fdb8a4272d9426b5">[href^="http://www.faceporn.net/free?"]
{display:none! important;}</style>`

See [issue #161](https://github.com/gorhill/uBlock/issues/161). The following filter is in [_EasyList_](https://easylist-downloads.adblockplus.org/):

    ##a[href^="http://www.faceporn.net/free?"]

This filter is classified internally by µBlock as a _high-medium generic_ filter. High generic filters are the most challenging to implement performance-wise. High-medium generic filters are implemented as follow: All the high-medium generic filters which matches the 8 first characters of the URL of a link on a web page will be seen as relevant to the web page and thus a CSS selector based on these filters will be injected in the web page, in order to hide the unwanted links. Now the above filter, as per implementation happens to match the ubiquitous links to `WWW.FACEbook.com`, and thus will be inserted as a CSS selector whenever links to Facebook are found on a web page.

Note that Adblock Plus also injects `a[href^="http://www.faceporn.net/free?"]` in every page, but unlike  µBlock, it is inserted in every page unconditionally, while µBlock tries as much as possible for performance-purpose to inject it only where it may be needed.

***

#### Feng Wang (Chrome store, 26 August 2014)

> 经常性的导致网页net::ERR_BLOCKED_BY_CLIENT
> 换回ADB [3-star rating]

Google translate:

> Frequent causes web `net::ERR_BLOCKED_BY_CLIENT`
> Exchange ADB

It's what is logged in the dev console when net requests are blocked. This is actually a **good** thing, this proves the extension does what it says it does -- blocking.

Adblock Plus will also causes `net::ERR_BLOCKED_BY_CLIENT` to be logged for each net request it blocks, it's no different.

***

#### Robert Lillywhite2 (Chrome store, 24 August 2014)

> At the start, this did what I wanted it to. I unfortunately have some adware on my laptop, which I can't get rid of and is annoying. This blocker stopped the adware doing anything on Chrome, but the other day it just stopped working. I uninstalled and reinstalled it and installed several other blockers, however none do what I want. This is just a slightly lighter version of other adblockers. [1-star rating]

Sorry about your adware/malware. µBlock is a blocker, it's purpose is not to scan and clean your PC. It makes no sense to expect µBlock to do so. You will have to fix your adware/malware problem with a proper tool, blaming µBlock won't fix your real problem.

***

#### Davis Graham (Chrome store, 18 August 2014)

> It's ok but there better ones out there. [1-star rating]

Ok. I am willing to work to improve it though. But I do realize that regardless how I try to make it better, there will always be people ready to rate as low as possible. I mean some people disliked [this](https://www.youtube.com/watch?v=IIJzCeYsy2c), or [this](https://www.youtube.com/watch?v=DlJ0ATDkxko), so an uninspiring computer tool which will be remembered by nobody in some near future is orders of magnitude more likely to be completely thumbed down.

***

#### Barfin Bob (Chrome store, 24 June 2014)

> Scrambles several websites I visit: Star-Telegram comment section in particular, slows down page loading, and the developer is an unknown. Uninstalled. [1-star rating]

The problem with the comment section at [Star-Telegram](http://www.star-telegram.com/) is due to the use of _EasyPrivacy_ list. I found the problem also occurs with _Adblock Plus_ if _EasyPrivacy_ is checked. ([test page](http://www.star-telegram.com/2014/06/24/5922649/us-plans-child-migrant-processing.html) where I spotted the problem.)

June 28: Found that problem is that `http://media.star-telegram.com/mistats/sites/dfw/startelegram.js` is being filtered by `/mistats/*` in _EasyPrivacy_. `@@||media.star-telegram.com/mistats/sites/dfw/startelegram.js^$domain=star-telegram.com` has been added to the project's own filters to fix the problem.
