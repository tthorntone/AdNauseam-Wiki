I can't answer to the review in web stores. It's unfortunate as sometimes I could help fix the problem(s), or correct inaccuracies, but the review area is not a forum, so I understand the limitations. Still, I will answer here to those reviews for which I have something meaningful to say.


***

#### Bryan Smith (Chrome store, 15 October 2014)

> It filters out too much, so I am constantly having to whitelist things (like instapaper.com?). Great performance, but too twiddly for me. [2-star rating]

µBlock will block according to whatever filter lists are selected. If it blocks too much, remove the filter lists you do not want. If it doesn't block enough, add the filter lists you want. Most filter lists are maintained by 3rd-parties, so if one filter list blocks something which you believe should not be blocked, bring the issue to the maintainer(s).

I did try specifically [instapaper.com](https://instapaper.com), and it appears it was working just fine. Whatever is not working should be brought as an issue.

I personally use [more than the default filter lists](https://github.com/gorhill/uBlock/wiki/Filter-lists:-gorhill), and I barely have to whitelist any site, so I am rather skeptical at the claims of _"constantly having to whitelist"_.

***

#### Павел Базута (Chrome store, 2 October 2014)

> Программа врет ! Даже проверил! Она всегда будет показывать на 2-3 единицы больше заблокированных реклам чем к примеру Adblock Потому что в ней специально так сделано , мол смотрите она лучше проверьте даже сами! в главном меню гугл хрома! Продолжаю дальше пользоваться Adblock - он не заменим!!!!

I have no idea what the topic is (the translation by Google Translate is of no help), but the first sentence, _"Программа врет !"_, translates into _"The program is lying!"_ (as per Google Translate).

My answer: No, I am not lying. If I could understand the issue, I am sure I could provide a better answer to counter the unsubstantiated accusation.

***

#### David A (Chrome store, 14 September 2014)

> Now I know why the cpu and memory is so low. This crap doesnt even save ad filters permanently. Even the ones you subscribed to. little ads come back when you refresh the page. Refresh a page again and they are gone? Its like its playing hide and go seek. [2-star rating]

The reason the memory and CPU is low (thanks for noticing) is the code was written from scratch with performance in mind, using benchmarks to drive development. It supports almost 100% of Adblock Plus filter syntax. The behavior your are seeing is not normal. If you could give me a URL where the problem occurs (see it as your contribution to the project), I could investigate.

***

#### Chris Whitaker (Chrome store, 2 September 2014)

> Going to have to agree with another reviewer - this blocker is great on memory usage, but blocks many other fields (i.e. my insurance company's login fields, the Target.com search box).  [...] [4-star rating]

Just to highlight how important it is to be specific when something doesn't work... Here I am given something **specific**: _"blocks [...] the Target.com search box"_. So **now** I can investigate. Well, the problem exists also with Adblock Plus, as the issue is caused by a filter in _EasyPrivacy_. Thus to workaround that filter which break target.com, [I created an exception filter](https://github.com/gorhill/uBlock/commit/6cc70d5c284f14e0c5fb2aa6c0fe184d6347b843) to cancel the one causing problem in _EasyPrivacy_.

µBlock has no control over _EasyList_, _EasyPrivacy_, these are hosted on Adblock Plus server.

***

#### Paul Kelly (Chrome store, 2 September 2014)

> This is a very good blocker that needs refinement. It blocks too many non-ad fields, such as blanks to enter passwords and usernames. This app could be the best with tweaks, but AdBlock Plus remains the reference standard. [4-star rating]

µBlock enforces Adblock Plus's _EasyList_ and _EasyPrivacy_, so if µBlock blocks more stuff than Adblock Plus with the **same filter lists** (_EasyList_ + _EasyPrivacy_, as per [EFF's advice](https://www.eff.org/deeplinks/2012/04/4-simple-changes-protect-your-privacy-online)), then this is a bug and it should be reported with appropriate details so that I can reproduce it, investigate it and fix it. I can't fix things which I am not aware are broken.

***

#### _Review removed_ (Chrome store, 1 September 2014)

> При запуске в коде страницы появляется вставка на какой то сайт hxxp://www.faceporn.net/free `<style id="ublock-preload-1ae7a5f130fc79b4fdb8a4272d9426b5">[href^="http://www.faceporn.net/free?"]
{display:none !important;}</style>` [1-star rating]

Google translate:

> When you run the code page appears insert on what that's hxxp://www.faceporn.net/free `<style id="ublock-preload-1ae7a5f130fc79b4fdb8a4272d9426b5">[href^="http://www.faceporn.net/free?"]
{display:none! important;}</style>`

See [issue #161](https://github.com/gorhill/uBlock/issues/161). The following filter is in [_EasyList_](https://easylist-downloads.adblockplus.org/):

    ##a[href^="http://www.faceporn.net/free?"]

High generic filters are the most challenging to implement performance-wise. µBlock internally classifies high generic filters into three sub-categories, _high-low_, _high-medium_ and _high-high_ generic. The filter above is classified internally by µBlock as a _high-medium_ generic filter.

High-medium generic filters are implemented as follow: All the high-medium generic filters which matches the 8 first characters of the URL of a link on a web page will be seen as relevant to the web page and thus a CSS selector based on these filters will be injected in the web page, in order to hide the unwanted links. Now the above filter, as per implementation happens to match the ubiquitous links to `WWW.FACEbook.com`, and thus will be inserted as a CSS selector whenever links to Facebook are found on a web page.

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