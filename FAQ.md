# Frequently Asked Questions

####How?

* [How do I install AdNauseam?](#how-do-i-install-adnauseam)
* [How do I install a development release of AdNauseam?](#how-do-i-install-a-development-release-of-adnauseam)
* [Can I use AdNauseam with my current adblocker?](#can-i-use-adnauseam-with-my-current-adblocker)
* [Does AdNauseam block ads or just hide them?](#does-adnauseam-block-ads-or-just-hide-them)
* [How does AdNauseam "hide Ads"?](#how-does-adnauseam-hide-ads)
* [How does AdNauseam "click Ads"?](#how-does-adnauseam-click-ads)
* [How does AdNauseam "block malware"?](#how-does-adnauseam-block-malware)
* [How does AdNauseam estimate the click cost it shows in the menu and vault?](#how-does-adnauseam-estimate-the-click-cost-it-shows-in-the-menu-and-vault)
* [Does AdNauseam respect the browser's private-browsing/incognito modes?](#does-adnauseam-respect-the-browsers-private-browsingincognito-modes)
* [What is AdNauseam's performance like? Will it speed up or slow down my browsing?](#what-is-adnauseams-performance-like-will-it-speed-up-or-slow-down-my-browsing)
* [Are you also tracking my clicks on your own servers?](#are-you-also-tracking-my-clicks-on-your-own-servers)
* [Who can tell that I’m using AdNauseam?](#who-can-tell-that-im-using-adnauseam)
* [Does AdNauseam's automatic ad clicking create billable events for advertisers?](#does-adnauseams-automatic-ad-clicking-create-billable-events-for-advertisers)
* [Can I combine AdNauseam and TrackMeNot?](#can-i-combine-adnauseam-and-trackmenot)
* [Sometimes it appears that there are multiples of the same ad in the advault?](#sometimes-it-appears-that-there-are-multiples-of-the-same-ad-in-the-advault)
* [What is user tracking? How does tracking work?](#what-is-user-tracking-how-does-tracking-work)
* [I found a bug! What do I do now?](#i-found-a-bug-what-do-i-do-now)
* [How to build AdNauseam (for developers)](https://github.com/dhowe/AdNauseam/wiki/Building-AdNauseam-from-source-(for-developers))

####Why?

* [Do you oppose all advertising?](#do-you-oppose-all-advertising-or-only-advertising-you-believe-is-abusive-eg-tracking)
* [Isn't it safer just to use an adblocker? Why engage with ad-networks at all?](#isnt-it-safer-just-to-use-an-adblocker-why-engage-with-ad-networks-at-all)
* [What must advertisers do to win the trust of Internet users?](#what-must-advertisers-do-to-win-the-trust-of-internet-users)
* [What made you choose data obfuscation as the strategy here?](#what-made-you-choose-data-obfuscation-as-the-strategy-here)
* [Do you know of other similar obfuscation initiatives along these lines?](#this-is-interesting-do-you-know-of-other-similar-obfuscation-initiatives-along-these-lines)
* [How does AdNauseam's clicking differ from 'click-fraud'?](#how-does-adnauseams-clicking-differ-from-click-fraud)
* [But what about "good" sites who don't track -- doesn't AdNauseam also block their Ads?](#but-what-about-good-sites-who-dont-track----doesnt-adnauseam-also-block-their-ads)
* [What is the "end goal" of AdNauseam?](#what-is-the-end-goal-of-adnauseam-confusing-data-so-it-becomes-useless-for-advertisers-and-forces-them-to-react)
* [Is there a business model behind AdNauseam?](#is-there-a-business-model-behind-adnauseam-do-you-consider-yourself-a-business-or-is-it-solely-to-make-some-kind-of-a-statement-about-the-state-of-web-advertising)
* [What about "Native Advertising?"](#are-you-concerned-that-adblocking-technology-is-part-of-the-reason-companies-like-facebook-are-so-keen-to-deploy-native-advertising----ads-that-masquerade-as-editorial-content)


####Who?

* [Daniel C Howe](#daniel-c-howe)
* [Helen Nissenbaum](#helen-nissenbaum)
* [Mushon Zer-Aviv](#mushon-zer-aviv)

##How?

#### How do I install AdNauseam?
You can find AdNauseam for <a href="https://chrome.google.com/webstore/detail/adnauseam/hgfacieeomogkcchookiodlpppbcolha" target="_new">Chrome</a>,  <a href="https://addons.mozilla.org/en-US/firefox/addon/adnauseam/" target="_new">Firefox</a>, or <a href="https://addons.opera.com/en/extensions/details/adnauseam-2" target="_new">Opera</a>. Just click 'install' and get started... 

_Note: you should always disable other adblockers while using AdNauseam_

#### How do I install a development release of AdNauseam?
You can find AdNauseam development releases [here](https://github.com/dhowe/AdNauseam/releases/).
To install, follow the instructions for your browser of choice below: 

- **Chrome**
 1. Download a ["Chromium" release](https://github.com/dhowe/AdNauseam/releases/). Older ones come as .zip directories (unzip after downloading), the latest release is a .crx file. 
 2. In your Chrome Browser navigate to Chrome > Preferences. In the side bar select "Extensions".
 3. Drag the file you downloaded in i) and drop it over the open extension page. A notification will inform about the the permissions it asks for. Hit "Add extension". 

- **Firefox**

 Note: Dev releases of AdNauseam will only run on the Developer Edition of Firefox ([download](https://www.mozilla.org/en-US/firefox/developer/)). 

 Prepare Firefox:
  
  1. Open you Firefox Developer Edition and type `about:config` into the url bar. When asked, choose to accept the risks.
  2. In the config panel, search for `xpinstall.signatures.required`. Make sure the value is set to `false`.   
 
 Install AdNauseam:

  1. Download a ["Firefox" release](https://github.com/dhowe/AdNauseam/releases/). The file format is .xpi. 
  1. In the browser navigate to Tools > Add-ons. In the side bar select "Extensions.
  1. Drag the file you downloaded in step i) and drop it over the open extension page. A notification will inform about the the permissions it asks for. Click "Install". 


- **Opera**
 1. Download a ["Opera" release](https://github.com/dhowe/AdNauseam/releases/). The file format is .nex.
 2. In your Opera Browser navigate to Opera > Preferences. In the side bar select the *puzzle piece* symbol/"Extensions".
 3. Drag the file you downloaded in i) and drop it over the open extension page. A notification will inform about the the permissions it asks for. Click "Install". 

_Note: you should always disable other adblockers while using AdNauseam_

#### Can I use AdNauseam with my current adblocker?
It is possible, but since your adblocker will likely block some, or all, of the Ads AdNauseam is collecting, this is NOT recommended. For the best experience, you should disable other adblockers while using AdNauseam.

#### What is AdNauseam's performance like? Will it speed up or slow down my browsing?
Benchmarks are in progress, however it is safe to say that AdNauseam is faster and safer than using either Adblock Plus (and its variants), or using no blocker at all. On the other hand, it is slower than a high-quality adblocker like uBlock, as it must allow certain requests (in order to collect Ads) that uBlock is able to block. While it depends on the types of pages visited, in our subjective experience, the difference between browsing with AdNauseam and uBlock is minimal.

#### Are you also tracking my clicks on your own servers?
No, we do not collect any information on users whatsoever.

#### Does AdNauseam block ads or just hide them?
Most adblockers (including uBlock, AdBlock-Plus, etc.) work via a combination of blocking and hiding strategies. Requests for some ads are blocked outright, while other Ads (text-only Ads,like those found on Google Search, are one common example) are first downloaded, then made invisible on the page. This is also how AdNauseam works. We simply treat image-Ads as if they were text-only Ads. And just like other adblockers, AdNauseam _does_ block malware and non-visual trackers.

#### Who can tell that I’m using AdNauseam?

Various parties may be able to detect AdNauseam, including websites (with Ads) that you visit, advertisers, and and Ad-networks (there may be additional parties behind the scenes of which we are not aware.) If they detect enough users, we hope they will get the message. AdNauseam and systems like it allow users to communicate their dissatisfaction directly, unmediated by vested interests who might claim to speak on our behalf.

#### Does AdNauseam's automatic Ad-clicking create billable events for advertisers?

It depends on the advertising business model and the degree of effort they are willing to put into filtering. Some might, others would not.

#### How does AdNauseam estimate the click cost it shows in the menu and vault?
[Pay-per-Click (PPC)](https://en.wikipedia.org/wiki/Pay_per_click) is a common internet advertising model in which advertisers pay for individual clicks on Ads.  The cost involved varies widely depending on a number of factors. One important factor is the type of website the Ad appears on; whether a normal 'display' website, or a 'search' website where the Ads shown are based on the user's query. The latter is generally more effective, with prices commonly calculated on the spot through a real-time bidding system. Display Ads may use fixed prices or other pricing models to determine click cost. Depending on these and other factors, costs per click range from below 1$ to over $50.  As the precise cost generated by clicks is not visible to the client, AdNauseam calculates an estimate using an average value of $1.58 for each clicked Ad. This value is taken from [this analysis](https://www.hochmanconsultants.com/cost-of-ppc-advertising/), in which various advertising models and platforms are taken into account.  

- [Additional info on the cost of Google's Adwords](http://www.wordstream.com/blog/ws/2015/05/21/how-much-does-adwords-cost)
- [Visualisation of _other_ costs imposed by targeted advertising](http://www.nytimes.com/interactive/2015/10/01/business/100000003949287.mobile.html) 

#### How does AdNauseam "hide Ads"?

In contrast to other blockers, AdNauseam does not block conventional, visual Ads, but hides them instead (when configured by the user to do so). This does not prevent such resources from being downloaded, but only impacts the way the page is rendered in your browser.  This is done as safely as possible, with cookies, and other identifiers disabled (by default) for all Ad requests. 

Once an Ad has been detected, CSS is used to render it invisible and to collapse the surrounding DOM if necessary. The rules for Ad detection are stored in a wide range of community-sourced and managed filter lists, each of which may be  enabled or disabled in the 3rd-party-filters panel. Additionally, hiding itself may be disabled, either globally, for a site, or for a page, via the settings panels.

#### How does AdNauseam "click Ads"?

AdNauseam 'clicks' Ads by issuing an HTTP request to the URL to which they lead. In current versions the is done via an XMLHttpRequest (or AJAX request) issued in a background process. This lightweight request signals a 'click' on the server responsible for the Ad, but does so without opening any additional windows or pages on your computer. Further it allows AdNauseam to safely receive and discard the resulting response data, rather than executing it in the browser, thus preventing a range of potential security problems (rogue Javascript or Flash code, XSS-attacks, etc.) caused by malfunctioning or malicious Ads. AdNauseam's clicking behaviour can be de-/activated in the settings panel.


#### How does AdNauseam "block malware"?

While visual Ads are not usually blocked by AdNauseam, non-visual trackers as well as potentially malicious content, can be blocked altogether. The detection of domains known to deliver such content is managed in the same set of user-configurable filter lists used to detect visual Ads. Additionally, AdNauseam's blocking behavior can be de-/activated in the settings panel, either for a site, a page, or globally (though this last option is strongly discouraged).

#### Does AdNauseam respect the browser's private-browsing/incognito modes?
Yes, AdNauseam does not detect Ads that occur on pages loaded in [private-browsing](https://support.mozilla.org/en-US/kb/private-browsing-use-firefox-without-history) or [incognito](https://support.google.com/chromebook/answer/95464?hl=en) windows.

#### Can I combine AdNauseam and [TrackMeNot](https://cs.nyu.edu/trackmenot/)?

Absolutely -- these two extensions should work happily together...

#### What is user tracking? How does tracking work?

When you visit a webpage, parts of the page may come from domains and servers other than the one you asked to visit. This is an essential feature of the web, but it has also come to be a _serious_ privacy problem. Nowadays embedded images and code often use cookies, fingerprinting, and other methods to track your browsing habits — often in order to display targetted advertisements. The domains that do this are called "third party trackers".You can read more about how they work on the excellent [EFF page](https://www.eff.org/deeplinks/2009/09/online-trackers-and-social-networks).


#### Sometimes it appears that there are multiples of the same Ad in the AdVault?

This sometimes happens. AdNauseam tests for Ad uniqueness of image-Ads by comparing the URLs of the displayed image. However, some Ad networks use different URLs in different Ads for the same image resource (often, but not always, with some additional tracking data in the query-string). In such cases, there is no simple/efficient way for AdNauseam to recognize that the images are the "same". One proposal for how to deal with this was suggested [here](https://github.com/dhowe/AdNauseam/issues/631).

#### I found a bug! What do I do now?

First, please make sure the bug hasn't already been reported by checking the current [bug list](https://github.com/dhowe/AdNauseam/issues).  If the bug hasn't yet been reported you can report it there. If you don't have a GitHub account, please create one so that we can communicate with you about the bug and fix it more quickly.

If you're not comfortable creating or don't want to create a GitHub account, you can also report the bug to adnauseam@rednoise.org.

##Why?

#### Do you oppose all advertising or only advertising you believe is abusive (e.g., tracking)?

We do not oppose online advertising categorically. We are attempting to bring to light a system that has taken over the web, whereby Ads are just the tip of the iceberg and serve as a delivery system for a massive back-end surveillance architecture that tracks us from site to site. It is not advertising we are protesting, but advertising insofar as it represents a dominant means of tracking users without their consent.

####Isn't it safer just to use an adblocker? Why engage with ad-networks at all?

Indeed it is marginally safer for one to simply use a strong adblocker and protect themselves. And it is also safer to stay at home rather than to attend a protest. But safety is not the only concern. Using an adblocker does little to change the status quo (especially not for those users without the resources to install/configure one, and so remain at risk). AdNauseam, and the obfuscation strategy in general, instead presents a possible avenue for collective resistance; a means of questioning and perhaps, eventually, changing the system. But this is not for everyone. If your goal is primarily self-protection, it may not be for you...

####  What must advertisers do to win the trust of Internet users?

There are various ways the status quo could be improved without damaging the Web ecosystem, e.g. contextual advertising, genuine adoption of a [meaningful Do Not Track standard](https://www.eff.org/dnt-policy), or client-side ad profiling (see [Adnostic](http://crypto.stanford.edu/adnostic/)). Alternatively, web-sites and publishers might switch to ad-networks that don't violate the privacy of users ([Deck](http://decknetwork.net/privacy/) appears to be one such example).

#### What made you choose data obfuscation as the strategy here?

We believe obfuscation is an important form of resistance to data tyranny. It can frustrate surveillance, help users to express their discontent, and act as a communal, rather than merely individual, practice.  (For further discussion, see References [coming soon])

#### This is interesting, do you know of other similar obfuscation initiatives along these lines?
There are many such instance, both in digital media and beyond. Please see the following articles ([1](http://firstmonday.org/article/view/3493/2955), [2](http://www.aprja.net/?p=2510)) for a range of examples.

#### How does AdNauseam's clicking differ from 'click-fraud'?

We understand what click-fraud is and do not believe we are engaging in it (nor do the lawyers we have consulted). Turning the tables, we would like to hear why someone holds that AdNauseam _does_ commit click fraud. Would they say the same of anyone who clicks on an Ad in which they are not really interested?

Click-Fraud:  "The practice of repeatedly clicking on an advertisement hosted on a website with the intention of generating revenue for the host site or draining revenue from the advertiser." (from http://clickfraud.org)

#### But what about "good" sites who don't track -- doesn't AdNauseam also block their ads?

Actually, blocking is controlled completely by the adblocker (uBlock-origin in version 2.x or greater), not by AdNauseam. We very much agree that users should be allowed to 'whitelist' whatever sites they want to support, and thus we will not configure AdNauseam to work with any adblockers that don't provide this functionality. To learn how to add a site to your whitelist, see this [page](https://github.com/dhowe/AdNauseam/wiki/Whitelisting).

#### What is the "end goal" of AdNauseam? Confusing data so it becomes useless for advertisers and forces them to react?

Yes, one goal of AdNauseam is protecting users from privacy violations and other harms that might follow directly or indirectly from tracking to which they have not consented. Another goal is to provide a means for users to let advertisers know that they don’t think such a system is ok. So yes, we would love to advertisers to respond with constructive alternatives which respect the values and preferences of users, but we are not holding our breath -- it may be that very different ways of supporting online content will need to be developed. But the real end goal of AdNauseam is to make software like AdNauseam unnecessary.

#### Is there a business model behind AdNauseam? Do you consider yourself a business, or is it solely to make some kind of a statement about the state of web advertising?

There is no business model behind AdNauseam. It is simply an attempt by concerned individuals to address abuses against users by powerful corporate entities. The software is and will remain free and open-source and will never surreptitiously collect data on users.

#### Are you concerned that adblocking technology is part of the reason companies like Facebook are so keen to deploy "native advertising" -- Ads that masquerade as editorial content?

We can't answer for Facebook's decisions to insert advertising material inadvertently into other content, Media companies have utilized this approach before and will likely continue to attempt to confuse individuals into paying attention with new techniques, once resistance has developed to entrenched methods. In print media, some governments have found the practice sufficiently unethical to require publishers clearly to distinguish advertising from editorial content.

##Who?

####Daniel C Howe

Daniel is an artist, researcher and critical technologist based in New York and Hong Kong. He leads all development on the project. You can contact him on Twitter at [@danielchowe](http://twitter.com/danielchowe) or by email at daniel [@] rednoise.org

####Helen Nissenbaum

Helen is a leading scholar of digital privacy at New York University. She is an advisor on the project and even wrote [a book inspired by it](https://mitpress.mit.edu/books/obfuscation). You can contact her at helen.nissenbaum [@] nyu.edu

####Mushon Zer-Aviv

Mushon is a designer, educator and media activist based in Tel Aviv. Mushon leads the design on AdNauseam. You can contact him on Twitter at [@mushon](http://twitter.com/mushon) or by email at mushon [@] shual.com