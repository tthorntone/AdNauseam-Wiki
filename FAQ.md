# Frequently Asked Questions

####How?

* [How do I install AdNauseam in Firefox?](#how-do-i-install-adnauseam-in-firefox)
* [Are you also tracking my clicks on your own servers?](#are-you-also-tracking-my-clicks-on-your-own-servers)
* [Does AdNauseam respect Firefox's private-browsing mode"?](#does-adnauseam-respect-the-browsers-private-browsing-mode)
* [Does AdNauseam block ads or just hide them?](#does-adnauseam-block-ads-or-just-hide-them)
* [Who can tell that I’m using AdNauseam?](#who-can-tell-that-im-using-adnauseam)
* [Does AdNauseam's automatic ad clicking create billable events for advertisers?](#does-adnauseams-automatic-ad-clicking-create-billable-events-for-advertisers)
* [Sometimes it appears that there are multiples of the same ad in the advault?](#sometimes-it-appears-that-there-are-multiples-of-the-same-ad-in-the-advault)

####Why?

* [Do you oppose all advertising?](#do-you-oppose-all-advertising-or-only-advertising-you-believe-is-abusive-eg-tracking)
* [What must advertisers do to win the trust of Internet users?](#what-must-advertisers-do-to-win-the-trust-of-internet-users)
* [What made you choose data obfuscation as the strategy here?](#what-made-you-choose-data-obfuscation-as-the-strategy-here)
* [Do you know of other similar obfuscation initiatives along these lines?](#this-is-interesting-do-you-know-of-other-similar-obfuscation-initiatives-along-these-lines)
* [How does AdNauseam's clicking differ from 'click-fraud'?](#how-does-what-the-adnauseams-clicking-differ-from-click-fraud)
* [But what about "good" sites who don't track their users -- doesn't AdNauseam also block their ads?](#but-what-about-good-sites-who-dont-track-their-users----doesnt-adnauseam-also-block-their-ads)
* [What is the "end goal" of AdNauseam?](#what-is-the-end-goal-of-adnauseam-confusing-data-so-it-becomes-useless-for-advertisers-and-forces-them-to-react)
* [Is there a business model behind AdNauseam?](#is-there-a-business-model-behind-adnauseam-do-you-consider-yourself-a-business-or-is-it-solely-to-make-some-kind-of-a-statement-about-the-state-of-web-advertising)
* [What about "Native Advertising?"](#are-you-concerned-that-ad-blocking-technology-is-part-of-the-reason-companies-like-facebook-are-so-keen-to-deploy-native-advertising----ads-that-masquerade-as-editorial-content)

####Who?

* [Daniel C Howe](#daniel-c-howe)
* [Helen Nissenbaum](#helen-nissenbaum)
* [Mushon Zer-Aviv](#mushon-zer-aviv)

##How?

#### How do I install AdNauseam in Firefox?

1. On Firefox, install <a href="https://addons.mozilla.org/firefox/downloads/latest/585454/platform:3/addon-585454-latest.xpi?src=dp-btn-primary">AdNauseam</a>

2. Click away…

#### Are you also tracking my clicks on your own servers?
No, we do not collect any information on users whatsoever.

#### Does AdNauseam respect the Firefox's "[private-browsing](https://support.mozilla.org/en-US/kb/private-browsing-use-firefox-without-history) mode"? 
Yes, AdNauseam does not detect, visit, or log any ads that occur on pages loaded in private-browsing windows.

#### Does AdNauseam block ads or just hide them?
Most adblockers (including uBlock, AdBlock-Plus, etc.) work via a combination of blocking and hiding strategies. Requests for some ads are blocked outright, while other ads (text-ads are a common example) are first downloaded, then made invisible on the page. This is also how AdNauseam works. In a small number of cases, in order to access the properties of the ad and display it to the user, AdNauseam must hide elements that an adblocker might otherwise block.  

#### Who can tell that I’m using AdNauseam?

Various parties may be able to detect AdNauseam, including websites (with ads) that you visit, advertisers, and and ad-networks (there may be additional parties behind the scenes of which we are not aware.) If they detect enough users, we hope they will get the message. AdNauseam and systems like it allow users to communicate their dissatisfaction directly, unmediated by vested interests who might claim to speak on our behalf.

#### Does AdNauseam's automatic ad clicking create billable events for advertisers?

It depends on the advertising business model and the degree of effort they are willing to filter Some might, others would not.

#### Sometimes it appears that there are multiples of the same ad in the advault?

This sometimes happens. AdNauseam tests for ad uniqueness of image-ads by comparing the URLs of the displayed image. However, some ad networks use different URLs in different ads for the same image resource (often, but not always, with some additional tracking data in the query-string). In such cases, there is no simple/efficient way for AdNauseam to recognize that the images are the "same". One proposal for how to deal with this was suggested [here](https://github.com/dhowe/AdNauseam/issues/192).


##Why?

#### Do you oppose all advertising or only advertising you believe is abusive (e.g., tracking)?

We do not oppose online advertising categorically. We are bringing to light a system that has taken over the web, whereby ads are just the tip of the iceberg and serve as a delivery system for the massive back-end surveillance architecture that tracks us from site to site. To reiterate, it is not advertising we are protesting, but advertising insofar as it represents a dominant means of tracking.

####  What must advertisers do to win the trust of Internet users?
There are various ways the status quo could be improved without damaging the Web ecosystem, e.g.: contextual advertising, genuine adoption of a meaningful Do Not Track standard (i.e. not merely Do Not Target), and client-side ad profiling (see Adnostic: http://crypto.stanford.edu/adnostic/). 

#### What made you choose data obfuscation as the strategy here?

We believe obfuscation is an important form of resistance to data tyranny. It can frustrate surveillance, help users to express their discontent, and act as a communal, rather than merely individual, practice.  (For further discussion, see References [coming soon])

#### This is interesting, do you know of other similar obfuscation initiatives along these lines?
There are many such instance, both in digital media and beyond. Please see the following papers ([1](http://firstmonday.org/article/view/3493/2955), [2](http://www.aprja.net/?p=2510)) for a range of examples. 

#### How does AdNauseam's clicking differ from 'click-fraud'?

We understand what click-fraud is and do not believe we are engaging in it (nor do the lawyers we have consulted). Turning the tables, we would like to hear why someone holds that AdNauseam _does_ commit click fraud. Would they say the same of anyone who clicks on an ad in which they are not really interested?

Click-Fraud:  "The practice of repeatedly clicking on an advertisement hosted on a website with the intention of generating revenue for the host site or draining revenue from the advertiser." (from http://clickfraud.org)

#### But what about "good" sites who don't track their users -- doesn't AdNauseam also block their ads?

Actually, blocking is controlled completely by the adblocker (uBlock in version 2.x or greater), not by AdNauseam. We very much agree that users should be allowed to 'whitelist' whatever sites they want to support, and thus we will not configure AdNauseam to work with any adblockers that don't provide this functionality. To learn how to add a site to your whitelist, see this [page](https://github.com/dhowe/AdNauseam/wiki/Whitelisting).

#### What is the "end goal" of AdNauseam? Confusing data so it becomes useless for advertisers and forces them to react?

Yes, one goal of AdNauseam is protecting users from privacy violations and other harms that might follow directly or indirectly from tracking to which they have not consented. Another goal is to provide a means for users to let advertisers know that they don’t think such a system is ok. So yes, we would love to advertisers to respond with constructive alternatives which respect the values and preferences of users, but we are not holding our breath -- it may be that very different ways of supporting online content will need to be developed. But the real end goal of AdNauseam is to make software like AdNauseam unnecessary.

#### Is there a business model behind AdNauseam? Do you consider yourself a business, or is it solely to make some kind of a statement about the state of web advertising?

There is no business model behind AdNauseam. It is simply an attempt by concerned individuals to address abuses against users by powerful corporate entities. The software is and will remain free and open-source and will never surreptitiously collect data on users.

#### Are you concerned that ad-blocking technology is part of the reason companies like Facebook are so keen to deploy "native advertising" -- ads that masquerade as editorial content?

We can't answer for Facebook's decisions to insert advertising material inadvertently into other content, Media companies have utilized this approach before and will likely continue to attempt to confuse individuals into paying attention with new techniques, once resistance has developed to entrenched methods. In print media, some governments have found the practice sufficiently unethical to require publishers clearly to distinguish advertising from editorial content.

##Who?

####Daniel C Howe

Daniel is an artist, researcher and critical technologist based in New York and Hong Kong. He leads all development on the project. You can contact him on Twitter at [@danielchowe](http://twitter.com/danielchowe) or by email at daniel [@] rednoise.org

####Helen Nissenbaum

Helen is a leading scholar working on themes of digital privacy at New York University. She is an advisor on the project and even wrote [a book inspired by it](https://mitpress.mit.edu/books/obfuscation). You can contact her at helen.nissenbaum [@] nyu.edu

####Mushon Zer-Aviv

Mushon is a designer, educator and media activist based in Tel Aviv. Mushon leads the design on AdNauseam. You can contact him on Twitter at [@mushon](http://twitter.com/mushon) or by email at mushon [@] shual.com