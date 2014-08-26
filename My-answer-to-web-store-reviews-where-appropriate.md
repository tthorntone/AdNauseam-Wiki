I can't answer to the review in web stores. It's unfortunate as sometimes I could help fix the problem(s), or correct inaccuracies, but the review area is not a forum, so I understand the limitations. Still, I will answer here to those reviews for which I have something meaningful to say.

***

#### Feng Wang (Chrome store, 26 August 2014)

> 经常性的导致网页net::ERR_BLOCKED_BY_CLIENT
> 换回ADB [3-star rating]

> Frequently causes web `net::ERR_BLOCKED_BY_CLIENT`
> Exchange ADB" (Google translate)

It's what is logged in the dev console when net requests are blocked. This is actually a **good** thing, this proves the extension does what it says it does.

Adblock Plus will also causes `net::ERR_BLOCKED_BY_CLIENT` to be logged each net request it blocks, it's no different.

I'm at a loss for words.

***

#### Davis Graham (Chrome store, 18 August 2014)
> It's ok but there better ones out there. [1-star rating]

Ok. I am willing to work to improve it though. But I do realize that regardless how I try to make it better, there will always be people ready to rate as low as possible. I mean some people disliked [this](https://www.youtube.com/watch?v=IIJzCeYsy2c), or [this](https://www.youtube.com/watch?v=DlJ0ATDkxko), so an uninspiring computer tool which will be remembered by nobody in some near future is orders of magnitude more likely to be completely thumbed down.

***

#### Barfin Bob (Chrome store, 24 June 2014)
> Scrambles several websites I visit: Star-Telegram comment section in particular, slows down page loading, and the developer is an unknown. Uninstalled. [1-star rating]

**My answer:** The problem with the comment section at [Star-Telegram](http://www.star-telegram.com/) is due to the use of _EasyPrivacy_ list. I found the problem also occurs with _Adblock Plus_ if _EasyPrivacy_ is checked. ([test page](http://www.star-telegram.com/2014/06/24/5922649/us-plans-child-migrant-processing.html) where I spotted the problem.)

June 28: Found that problem is that `http://media.star-telegram.com/mistats/sites/dfw/startelegram.js` is being filtered by `/mistats/*` in _EasyPrivacy_. `@@||media.star-telegram.com/mistats/sites/dfw/startelegram.js^$domain=star-telegram.com` has been added to the project's own filters to fix the problem.
