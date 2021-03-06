I can't answer to the review in web stores. It's unfortunate as sometimes I could help fix the problem(s), or correct inaccuracies, but the review area is not a forum, so I understand the limitations. Still, I will answer here to those reviews for which I have something meaningful to say.

***

#### Kim Visnes (Chrome store, 17 May 2015)

> It tries to inject scripts into Twitter. And I can't seem to find out why it does this. It's the only website I've seen it try to do it with. [1-star rating]

Completely false. uBlock **does not** inject `script` tags in web pages, it  only injects *inline* `style` tags -- to hide DOM elements as per cosmetic filters.

I also responded to this user [on Twitter](https://twitter.com/gorhill/status/600292965114900480). So far he did not take my offer to investigate his issue by reporting it on GitHub.

***

#### Kougeru ([AMO](https://addons.mozilla.org/en-US/firefox/addon/ublock/reviews/696982/), 8 April 2015)

> Personal tests show ublock using 1.7 MBs after over 24 hours of my browser running. Adblock Plus was using 15 MBs. That may seem like a big difference, however it is not

This user's findings are flawed, for many reasons.

First, there is no way uBlock consumes only 1.7 MB. I suspect this user used [_about:addons-memory_](https://addons.mozilla.org/en-us/firefox/addon/about-addons-memory/) extension to draw his conclusion.

Problem with _about:addons-memory_ is that it doesn't show all the memory used by an extension. uBlock has two counterparts listed in the `about:memory` results. The smallest figure is listed under 
`add-ons`. The bigger figure is listed under `window-objects > resource://gre-resources/hiddenWindow.html, id=1)`.

Still, taking this into account, uBlock has a smaller memory footprint than ABP, even when using many more filter lists (something else to take into account).

But the biggest problem with this user's conclusion is that he doesn't take into account the [contributed memory footprint to web pages](https://github.com/gorhill/uBlock/wiki/Firefox-version:-benchmarking-memory-footprint). That memory is not counted as being used by an extension, but rather as being used by web pages thenmselves.

This contributed memory is where ABP [suffers the most](https://bugzilla.mozilla.org/show_bug.cgi?id=988266#c6). ABP will inject 14,000+ CSS rules into every page **and** into every `iframe` on a page. The count can easily reach  21,000+ CSS rules if using more than just EasyList (i.e. Fanboy's Social).

On the other hand, uBlock will typically inject from none to a handful of CSS rules.

***

#### Earl Baugh (Chrome store, 25 February 2015)

> Prevents web sites from working properly, i.e. Capitol One 360, you can't login with this enabled. [...] If I turn off ALL the filters I can get some things to work. **But adding in ANY filters kills things like logging into Capitol One.**

Bolded statement is completely false.

EasyPrivacy is the filter list which prevents logging in on Capital One 360. The normal course of action is to report the problem to [EasyPrivacy maintainers](https://forums.lanik.us/viewforum.php?f=64), and/or to disable that filter list. Once it is disabled, you can log in on Capitol One 360.

Adblock Plus + EasyPrivacy also breaks logging into Capital One 360.

I reported the problem with EasyPrivacy to the maintainers: <https://forums.lanik.us/viewtopic.php?f=64&t=21247>, so you will benefit the fix with Adblock Plus as well should you enable EasyPrivacy in it.

***

#### kreemoweet ([mozillazine.org](http://forums.mozillazine.org/viewtopic.php?p=14029145#p14029145), 17 February 2015)

> [...] the ??Block developer has been caught making false statements about his app and other adblockers

Vague claim, no specifics. No answer so far when asked to substantiate claim.

***

#### Connor W. (Chrome store, 27 January 2015)

> It is very lighweight, but it blocked a ton of stuff that wasn't ads. For example, on Google Translate, it blocked all the alternate translations and said it was blocking 225 ads! [2-star rating]

I just tested Google Translate with ??Block + default filter lists, and I could select alternate translations without any problem.

Trying to reproduce the reported issue, I selected _"Fanboy???s Annoyance List???"_ and _"Fanboy???s Enhanced Tracking List???"_: **still no issue**.

Regarding the high count ("225 ads!"): again, ??Block is not an **"ad blocker**," it's a **blocker**, so it will also block according to the filters in _EasyPrivacy_, and in the current case a lot of network requests to `translate.google.*` are blocked because of the filter `||google.*/gen204?` in _EasyPrivacy_.

***

#### [David H. Mason](https://plus.google.com/118169340317846488874/posts) (Chrome store, 10 January 2015)

> The author says it should operate identically to adblock. However, there are many, many sites which do not work with ??Block that work fine with adblock. For an example (among many),try the map view at https://nomadlist.io/. For me at leas,t it does not work with ??Block, but it's fine without or with adblock. [1-star rating]

The map view also breaks without any blocker, or with Adblock Plus, and I get it working with ??Block. It looks like it's random, but whatever it is, it's not because of any blocker, since it happened also without any blocker.

No thanks for quickly jumping to baseless conclusions.

**Update:** Reviewer modified his review on January 11 2015:

> [...] For an example (among many),try http://forum.notebookreview.com/lenovo/613094-x220-max-ram-8gb-16gb.html. For me at least, it does not work with ??Block, but it's fine without or with adblock.

That site is completely broken, and ??Block has nothing to do with this:

![figure 1](https://raw.githubusercontent.com/gorhill/uBlock/master/doc/img/chrome-store-david-h-mason.png)

That's the same URL, but using Adblock Plus. I get the same result without any blocker. Same result on Firefox. Etc.

***

#### Michael Chadwick (Chrome store, 31 December 2014)

> I had spend hours upon hours trying to get rid of several adware infections (Obrona, Offers4u, SASA). I tried malware/adware/spyware removers, antivirus scans, uninstall utilities, system resets. This is the only thing that got rid of them for me. A tip: go into the extension options and check off all the filters - there were still a few ad panels that appeared before I did that. [5-star rating]

??Block's purpose is **not** to remove existing malware/adware/spyware: It can not do this.

??Block's purpose is to block outgoing network requests, and collapse [DOM](http://en.wikipedia.org/wiki/Document_Object_Model) elements according to the selected filter lists.

It appears you are merely curing the symptoms, not the disease. I wouldn't want users to get false expectations concerning ??Block.

***

#### [Brian Flores](https://plus.google.com/+BrianFloresGoesTo11) (Chrome store, 15 December 2014)

> Not as lightweight as claimed. Absolutely jams on certain sites, the block counter spiralling and the browser window virtually locked up. Needlessly blocks icons. [2-star rating]

Yes it is as lightweight as claimed. I run detailed benchmarks. You counter with no data + methodology.

Making such claim as "absolutely jams on certain sites" without caring one bit about substantiating this claim by providing a specific URL with which the issue you report could be investigated is highly dubious.

Given the hundreds of hour of work put into this [libre software](http://en.wikipedia.org/wiki/Free_software) by me and contributors, certainly you could have taken the _few seconds_ necessary to post an actual test case (i.e. a URL) to substantiate your issue, which appears rather specific to you (nothing like this was ever reported before).

And regarding "needlessly blocks icons": ??Block blocks according to the selected third-party filter lists. If you think it blocks too much, disable whatever filter lists you want.

#### [Philip Jordan](https://plus.google.com/110005867636099468435) (Chrome store, 9 December 2014)

> This extension is overkill, it seems to do more harm than good. It is over zealous for what is should do. Had to remove it as it was causing more harm than good to my surfing experience. Going back to ABP or just may remove them all together. [2-star rating]

??Block parses and enforces the same filter syntax as Adblock Plus. So just un-select whatever filter lists which you think is not needed. You can keep only _EasyList_ if you wish (i.e. Adblock Plus' default), this way ??Block will use even less CPU and memory resource.

Some users prefer blocking more than ??Block's default selection of filter lists, some users prefer blocking less than ??Block's default selection of filter lists. _The only thing left to do for these users is to select/un-select whatever filter lists they want._

***

#### Robert Utner (Chrome store, 4 December 2014)

> Seiten laden schneller als mit ABP, aber unzuverl??ssiger und Chrome frisst mehr CPU im leerlauf. [2-star rating]

Google Translate:

> Pages load faster than with ABP, but unreliable and Chrome eats more CPU idle in.

"Unreliable" in what sense? No details. ??Block enforces the filters used by ABP.

??Block doesn't consume more CPU cycle than ABP on idle. The reviewer should post **real** benchmark data along with methodology, as rigorous as the ones I have been constantly running to develop ??Block. The reviewer's unsubstantiated comment goes counter to the benchmark I've been running.

***

#### Joshua Nicholson (Chrome store, 2 November 2014)

> Please remove the default setting of blocking social media, not every techie is anti-social. [4-star rating]

I see this from a different angle.

_"Fanboy's Social Block List"_ is included in order to reduce privacy-exposure. Using that one filter list has nothing to do with being "anti-social", its useful purpose from ??Block's perspective is of being a privacy-enhancing filter list.

In any case, it's easy to un-select it.

***

#### Etienne Levesque Guitard (Chrome store, 20 October 2014)

> Fast but overly zealous blocker. Blocks much more than ads, like Google Analytics, Google and Facebook-based single sign-ons, etc.
> I just want an ad blocker. [2-star rating]

Then just un-select all lists except _EasyList_ from the _"3rd-party filters"_ in the dashboard. This way you will end up with an ad blocker which is even leaner and faster.

***

#### Bryan Smith (Chrome store, 15 October 2014)

> It filters out too much, so I am constantly having to whitelist things (like instapaper.com?). Great performance, but too twiddly for me. [2-star rating]

??Block will block according to whatever filter lists are selected. If it blocks too much, remove the filter lists you do not want. If it doesn't block enough, add the filter lists you want. Most filter lists are maintained by 3rd parties, so if one filter list blocks something which you believe should not be blocked, bring the issue to the maintainer(s).

I did try specifically [instapaper.com](https://instapaper.com), and it appears it was working just fine. Whatever _specific_ is not working should be brought as an issue.

I personally use [more than the default filter lists](https://github.com/gorhill/uBlock/wiki/Filter-lists:-gorhill), and I barely have to whitelist any site, so I am rather skeptical at the claims of _"constantly having to whitelist"_.

***

#### ?????????? ???????????? (Chrome store, 2 October 2014)

> ?????????????????? ???????? ! ???????? ????????????????! ?????? ???????????? ?????????? ???????????????????? ???? 2-3 ?????????????? ???????????? ?????????????????????????????? ???????????? ?????? ?? ?????????????? Adblock ???????????? ?????? ?? ?????? ???????????????????? ?????? ?????????????? , ?????? ???????????????? ?????? ?????????? ?????????????????? ???????? ????????! ?? ?????????????? ???????? ???????? ??????????! ?????????????????? ???????????? ???????????????????????? Adblock - ???? ???? ??????????????!!!!

I have no idea what the topic is (the translation by Google Translate is of no help), but the first sentence, _"?????????????????? ???????? !"_, translates into _"The program is lying!"_ (as per Google Translate).

My answer: No, I am not lying. If I could understand the issue, I am sure I could provide a better answer to counter the unsubstantiated accusation.

[Translation from Russian by a contributor (thanks):]

> "The program is lying! I even checked it. It will always show 2-3 extra blocked ads compared to Adblock because it is how it's built, as if saying 'look, it is better, see for yourself!' In the main menu of Google Chrome! I will continue to use Adblock - it cannot be replaced!!!!"

With the same filter lists, ??Block and ABP will block the same amount of network requests. However ??Block comes with more filter lists selected out of the box, so as a result it will block more than ABP with default settings. ??Block has definitely more useful blocking potential than ABP: ??Block support hosts files, dynamic filtering, and also local mirroring helps prevent remote connections to various CDNs.

***

#### David A (Chrome store, 14 September 2014)

> Now I know why the cpu and memory is so low. This crap doesnt even save ad filters permanently. Even the ones you subscribed to. little ads come back when you refresh the page. Refresh a page again and they are gone? Its like its playing hide and go seek. [2-star rating]

The reason the memory and CPU is low (thanks for noticing) is the code was written from scratch with performance in mind, using benchmarks to drive development. It supports almost 100% of Adblock Plus filter syntax. The behavior your are seeing is not normal. If you could give me a URL where the problem occurs (see it as your contribution to the project), I could investigate.

***

#### Chris Whitaker (Chrome store, 2 September 2014)

> Going to have to agree with another reviewer - this blocker is great on memory usage, but blocks many other fields (i.e. my insurance company's login fields, the Target.com search box).  [...] [4-star rating]

Just to highlight how important it is to be specific when something doesn't work... Here I am given something **specific**: _"blocks [...] the Target.com search box"_. So **now** I can investigate. Well, the problem exists also with Adblock Plus, as the issue is caused by a filter in _EasyPrivacy_. Thus to workaround that filter which break target.com, [I created an exception filter](https://github.com/gorhill/uBlock/commit/6cc70d5c284f14e0c5fb2aa6c0fe184d6347b843) to cancel the one causing problem in _EasyPrivacy_.

??Block has no control over _EasyList_, _EasyPrivacy_, these are hosted on Adblock Plus server.

***

#### Paul Kelly (Chrome store, 2 September 2014)

> This is a very good blocker that needs refinement. It blocks too many non-ad fields, such as blanks to enter passwords and usernames. This app could be the best with tweaks, but AdBlock Plus remains the reference standard. [4-star rating]

??Block enforces Adblock Plus's _EasyList_ and _EasyPrivacy_, so if ??Block blocks more stuff than Adblock Plus with the **same filter lists** (_EasyList_ + _EasyPrivacy_, as per [EFF's advice](https://www.eff.org/deeplinks/2012/04/4-simple-changes-protect-your-privacy-online)), then this is a bug and it should be reported with appropriate details so that I can reproduce it, investigate it and fix it. I can't fix things which I am not aware are broken.

***

#### _Review removed_ (Chrome store, 1 September 2014)

> ?????? ?????????????? ?? ???????? ???????????????? ???????????????????? ?????????????? ???? ?????????? ???? ???????? hxxp://www.faceporn.net/free `<style id="ublock-preload-1ae7a5f130fc79b4fdb8a4272d9426b5">[href^="http://www.faceporn.net/free?"]
{display:none !important;}</style>` [1-star rating]

Google translate:

> When you run the code page appears insert on what that's hxxp://www.faceporn.net/free `<style id="ublock-preload-1ae7a5f130fc79b4fdb8a4272d9426b5">[href^="http://www.faceporn.net/free?"]
{display:none! important;}</style>`

See [issue #161](https://github.com/gorhill/uBlock/issues/161). The following filter is in [_EasyList_](https://easylist-downloads.adblockplus.org/):

    ##a[href^="http://www.faceporn.net/free?"]

The purpose of this filter is to **remove** links to `www.faceporn.net` from a web page.

High generic filters are the most challenging to implement performance-wise. ??Block internally classifies high generic filters into three sub-categories, _high-low_, _high-medium_ and _high-high_ generic. The filter above is classified internally by ??Block as a _high-medium_ generic filter.

High-medium generic filters are implemented as follow: All the high-medium generic filters which matches the 8 first characters of the URL of a link on a web page will be seen as relevant to the web page and thus a CSS selector based on these filters will be injected in the web page, in order to hide the unwanted links. Now the above filter, as per implementation happens to match the ubiquitous links to `WWW.FACEbook.com`, and thus will be inserted as a CSS selector whenever links to Facebook are found on a web page.

Note that Adblock Plus also injects `a[href^="http://www.faceporn.net/free?"]` in every page, but unlike  ??Block, it is inserted in every page unconditionally, while ??Block tries as much as possible for performance-purpose to inject it only where it may be needed.

***

#### Feng Wang (Chrome store, 26 August 2014)

> ????????????????????????net::ERR_BLOCKED_BY_CLIENT
> ??????ADB [3-star rating]

Google translate:

> Frequent causes web `net::ERR_BLOCKED_BY_CLIENT`
> Exchange ADB

It's what is logged in the dev console when net requests are blocked. This is actually a **good** thing, this proves the extension does what it says it does -- blocking.

Adblock Plus will also causes `net::ERR_BLOCKED_BY_CLIENT` to be logged for each net request it blocks, it's no different.

***

#### Robert Lillywhite2 (Chrome store, 24 August 2014)

> At the start, this did what I wanted it to. I unfortunately have some adware on my laptop, which I can't get rid of and is annoying. This blocker stopped the adware doing anything on Chrome, but the other day it just stopped working. I uninstalled and reinstalled it and installed several other blockers, however none do what I want. This is just a slightly lighter version of other adblockers. [1-star rating]

Sorry about your adware/malware. ??Block is a blocker, it's purpose is not to scan and clean your PC. It makes no sense to expect ??Block to do so. You will have to fix your adware/malware problem with a proper tool, blaming ??Block won't fix your real problem.

***

#### Davis Graham (Chrome store, 18 August 2014)

> It's ok but there better ones out there. [1-star rating]

Ok. I am willing to work to improve it though. But I do realize that regardless how I try to make it better, there will always be people ready to rate as low as possible. I mean some people disliked [this](https://www.youtube.com/watch?v=IIJzCeYsy2c), or [this](https://www.youtube.com/watch?v=DlJ0ATDkxko), so an uninspiring computer tool which will be remembered by nobody in some near future is orders of magnitude more likely to be completely thumbed down.

***

#### Barfin Bob (Chrome store, 24 June 2014)

> Scrambles several websites I visit: Star-Telegram comment section in particular, slows down page loading, and the developer is an unknown. Uninstalled. [1-star rating]

The problem with the comment section at [Star-Telegram](http://www.star-telegram.com/) is due to the use of _EasyPrivacy_ list. I found the problem also occurs with _Adblock Plus_ if _EasyPrivacy_ is checked. ([test page](http://www.star-telegram.com/2014/06/24/5922649/us-plans-child-migrant-processing.html) where I spotted the problem.)

June 28: Found that problem is that `http://media.star-telegram.com/mistats/sites/dfw/startelegram.js` is being filtered by `/mistats/*` in _EasyPrivacy_. `@@||media.star-telegram.com/mistats/sites/dfw/startelegram.js^$domain=star-telegram.com` has been added to the project's own filters to fix the problem.