I've seen so much misrepresentation and disinformation lately regarding µBlock (always from anonymous sources) that I will set the official record here.

Let's just say µBlock is a real threat to Adblock Plus owner's business model, Eyeo GmbH, and to those [who paid Eyeo GmbH](http://9to5google.com/2015/02/02/google-along-with-amazon-microsoft-reportedly-paying-adblock-to-unblock-ads/) to be part of the "acceptable ads" marketing campaign.

### Q. Does µBlock blocks ads or just hide them?

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
