I've seen an increase in misrepresentation and disinformation lately regarding µBlock -- and not surprisingly always from anonymous sources.

I will set the official record here.

First, let's just say µBlock is a real threat to Adblock Plus owner's business model, Eyeo GmbH, and to those [who paid Eyeo GmbH](http://9to5google.com/2015/02/02/google-along-with-amazon-microsoft-reportedly-paying-adblock-to-unblock-ads/) to be part of the "acceptable ads" marketing campaign. It is also a threat to other big-name blockers as well.

There seems to be underhanded attempts to discredit µBlock lately in various venues. Here is a typical comment: 

> uBlock who is recently found to not actually "block" ads, but rather hide them after its been displayed. Adblock actually blocks them before they can even display them.

The statement above is plain fear-using-disinformation. That kind of disinformation also happens to be convenient to the incumbent blockers, and also to those who have an interest in people using those incumbent blockers.

There are two kinds of [ABP-compatible filters](https://adblockplus.org/en/filters): network filters and cosmetic filters. _Cosmetic filters_ are referred to as _element hiding_ filters by Adblock Plus ("ABP").

#### Network filters

The purpose of network filter is to prevent a network request to be made to a remote server, so as to prevent downloading a remote resource. µBlock will prevent the network request from even being made. This saves bandwidth, decrease privacy exposure -- as the remote server won't be able to log anything if you do not contact it.

**Answer:** resources blocked.

#### Cosmetic filters

These filters serve to remove DOM element from a web page. They have no value privacy-wise, it is essentially to make web page look better by removing unwanted content, which usually cannot be blocked using network filters. Just like Adblock Plus, µBlock will hide DOM elements on a web page which match cosmetic filters.

**Answer:** resources hidden.

#### Hosts file

µBlock also support the parsing and enforcing of hosts files -- something which ABP does not. All entries in a hosts file are parsed as network filters, i.e. no resource will be fetch from a remote server which appear in a hosts file.

**Answer:** resources blocked.
