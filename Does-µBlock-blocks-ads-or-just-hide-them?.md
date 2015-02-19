I've seen an increase in misrepresentation and disinformation lately regarding µBlock -- and not surprisingly always from anonymous sources.

I will set the official record here.

First, let's just say µBlock is a real threat to Adblock Plus owner's business model, Eyeo GmbH, and to those [who paid Eyeo GmbH](http://www.theregister.co.uk/2015/02/02/google_amazon_taboola_microsoft_adplock_plus_unblock/) to be part of the "acceptable ads" marketing campaign. It is also a threat to other big-name blockers as well. Add to this [not everybody](https://forums.lanik.us/viewtopic.php?f=64&t=17842) [is pleased](https://github.com/gorhill/uBlock/issues/564) with µBlock enabling _EasyPrivacy_ by default.

There seems to be underhanded attempts to discredit µBlock lately in various venues. Here is a typical comment: 

> uBlock who is recently found to not actually "block" ads, but rather hide them after its been displayed. Adblock actually blocks them before they can even display them.

The statement above is plain fear-using-disinformation. That kind of disinformation also happens to be convenient to the incumbent blockers, and also to those who have an interest in people using those incumbent blockers.

There are two kinds of [ABP-compatible filters](https://adblockplus.org/en/filters): network filters and cosmetic filters. _Cosmetic filters_ are referred to as _element hiding_ filters by Adblock Plus ("ABP").

#### Network filters

**Short answer:** resources blocked: network requests are cancelled before they leave the browser.

The purpose of network filter is to prevent a network request to be made to a remote server, so as to prevent downloading a remote resource. µBlock will prevent the network request from even being made. This saves bandwidth, decrease privacy exposure -- as the remote server won't be able to log anything if you do not contact it.

#### Hosts file

**Short answer:** resources blocked: network requests are cancelled before they leave the browser.

µBlock also support the parsing and enforcing of hosts files -- something which ABP does not. All entries in a hosts file are parsed as network filters, i.e. no resource will be fetch from a remote server which appear in a hosts file, no connection will even be attempted.

#### Cosmetic filters

**Short answer:** resources hidden -- in various ways depending on the class of cosmetic filters.

These filters serve to remove DOM elements from a web page. They have no value privacy-wise, it is essentially to make web page look better by removing unwanted content, which usually cannot be blocked using network filters. Just like ABP, µBlock will hide DOM elements on a web page which match cosmetic filters. µBlock uses a [different method](https://github.com/gorhill/uBlock/wiki/Cosmetic-filtering-in-%C2%B5Block:-version-0.4.0.0-update) than other big-name blockers to hide the DOM elements though.

Different classes of cosmetic filters are applied differently:

- Specific cosmetic filters: injected before page's root DOM is loaded
    - No flickering
- Generic cosmetic filters: injected after page's root DOM is loaded
    - These are cacheable
    - Since these cosmetic filters are applied after page load, DOM elements **may** be hidden after they are rendered
    - Notice the emphasized "may": generally, you won't see this; and sometimes you will notice **more** flickering with ABP (with same filter lists):
    - Demonstration: [test page](http://raymondhill.net/ublock/tiles1.html)
        - Chromium + uBlock: minimal flickering (sometimes none)
        - Chromium + ABP: noticeable flickering
        - Firefox + uBlock: no flickering
        - Firefox + ABP: no flickering
- Cached generic cosmetic filters: injected before page's root DOM is loaded
    - No flickering