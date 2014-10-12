#### "µBlock is just a stripped-down version of HTTP Switchboard".

No. µBlock started off by extracting the pattern-filtering engines (net and cosmetic filters) from [HTTP Switchboard](https://github.com/gorhill/httpswitchboard#http-switchboard-for-chromium) ("HTTPSB"). These engines needed more work to bring them to maturity. Most of that work won't be ported back to HTTPSB. See ["The road ahead"](https://github.com/gorhill/httpswitchboard/issues/378) for details.

#### "The memory usage isn't actually ABP's fault, _EasyList_ is like 40,000+ lines of rules that all have to be parsed by ABP".

µBlock also parse _EasyList_, _EasyPrivacy_, _Malware domains_ lists, 
and _Peter Lowes's Ad server_ list out of the box and yet uses less than half the 
memory of [Adblock Plus](https://adblockplus.org/) ("ABP"), which is itself much more efficient than 
[AdBlock](https://getadblock.com/) (at least this is what I have measured on Chromium-based browsers).

#### "µBlock has all the features ABP has!"

µBlock is its own thing, it doesn't try to be Adblock Plus or any other.

Regular expression-based filters are not supported. At time of writing I see three such filters in _EasyList_, and none in _EasyPrivacy_. So rather uncommon. I may support them if there is really a need, but only for those which will have the `domain` filter option set: otherwise it's just impossible to implement efficiently such filters, and µBlock won't encourage their use by supporting these. For all the instances I have seen, it is possible to translate them into more efficient non-regex-based filters.

Filters with the `$elemhide` option are ignored. At time of writing, I see 50 such filters in _EasyList_. The purpose of these filters is to disable cosmetic filters on specific sites.

#### "ABP has all the features µBlock has!"

No. µBlock currently offers you more:

- [Extends the filter syntax](https://github.com/gorhill/uBlock/wiki/Filter-syntax-extensions).
- [Local mirroring](https://github.com/gorhill/uBlock/wiki/Experimental-features#privacy-exposure-reduction-local-mirroring), a currently experimental but promising feature.
- [Dynamic filtering](https://github.com/gorhill/uBlock/wiki/Dynamic-filtering), the ability to point-and-click to filter on/off `script` and `iframe` tags, on a 1st- or 3rd-party basis. I consider this to be a [key feature](https://github.com/gorhill/uBlock/wiki/Dynamic-filtering---examples) of µBlock.
- Element picker is more modern.
- Let you select most common filter lists out of the box, without the need to import them first.
- Supports hosts files
- Ability to whitelist single web page, or a whole section of a web site.
- Ability to not load cosmetic filters (saves lot of memory).
- A log of the net requests showing allowed/blocked net requests, and which filter, if any, matched each net request.

#### "µBlock has a smaller memory footprint than Ghostery or Disconnect."

No it doesn't. Last time I checked, µBlock has a larger memory footprint than both 
[Ghostery](https://www.ghostery.com) and [Disconnect](/disconnectme/disconnect). That's for their own memory footprint. I didn't look into their contributions to the memory footprint added to each web page.

Regarding CPU footprint, I don't know, I didn't measure yet (maybe I will), but my hunch at this point is that the CPU overhead is higher than that of µBlock. I did run [CPU benchmark a very long time ago](https://github.com/gorhill/httpswitchboard/wiki/Doesn't-HTTPSB-add-a-significant-overhead-to-network-traffic%3F), and this was the case -- but after such a long time, I have to assume things have changed and I would need to benchmark again -- a time-consuming task.

Keep in mind that µBlock, like ABP, Adguard, and some others allows users to enter their own filters, something not possible with Ghostery or Disconnect.

There are also other differences, or similarities: µBlock, _Disconnect_
and ABP are licensed under [GPL](http://en.wikipedia.org/wiki/GNU_General_Public_License). Also, there is [this](https://github.com/gorhill/uBlock/wiki/%C2%B5Block-and-others:-Blocking-ads,-trackers,-malwares).