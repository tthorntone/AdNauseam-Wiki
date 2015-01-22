#### "µBlock is just a stripped-down version of HTTP Switchboard".

No. µBlock started off by extracting the pattern-filtering engines (net and cosmetic filters) from [HTTP Switchboard](https://github.com/gorhill/httpswitchboard#http-switchboard-for-chromium) ("HTTPSB"). These engines needed more work to bring them to maturity. Most of that work won't be ported back to HTTPSB. See ["The road ahead"](https://github.com/gorhill/httpswitchboard/issues/378) for details.

#### "The memory usage isn't actually ABP's fault, _EasyList_ is like 40,000+ lines of rules that all have to be parsed by ABP".

µBlock also parse _EasyList_, _EasyPrivacy_, _Malware domains_ lists, 
and _Peter Lowes's Ad server_ list out of the box and yet uses less than half the 
memory of [Adblock Plus](https://adblockplus.org/) ("ABP"), which is itself much more efficient than 
[AdBlock](https://getadblock.com/) (at least this is what I have measured on Chromium-based browsers).

#### "µBlock has all the features ABP has!"

µBlock is its own thing, it doesn't try to be Adblock Plus or any other.

Regular expression-based filters are not supported. At time of writing I see three such filters in _EasyList_, and none in _EasyPrivacy_. So rather uncommon. I may support them if there is really a need, but only for those which will have the `domain` filter option set: otherwise it's just impossible to implement efficiently such filters, and µBlock won't encourage their use by supporting these.

For all the instances I have seen, it is possible to translate them into more efficient non-regex-based filters. For example, the following regex-based filters found in _EasyList_:

    /^https?\:\/\/(?!(connect\.facebook\.net|ajax\.cloudflare\.com|www\.google-analytics\.com|ajax\.googleapis\.com|fbstatic-a\.akamaihd\.net)\/)/$script,third-party,xmlhttprequest,domain=firedrive.com
    /^https?\:\/\/(?!(connect\.facebook\.net|ajax\.cloudflare\.com|www\.google-analytics\.com|ajax\.googleapis\.com|fbstatic-a\.akamaihd\.net|stats\.g\.doubleclick\.net|api-secure\.solvemedia\.com|api\.solvemedia\.com|sb\.scorecardresearch\.com|www\.google\.com)\/)/$script,third-party,xmlhttprequest,domain=mediafire.com
    /^https?\:\/\/(?!(connect\.facebook\.net|www\.google-analytics\.com|ajax\.googleapis\.com|netdna\.bootstrapcdn\.com|[\w\-]+\.addthis\.com|bp\.yahooapis\.com|b\.scorecardresearch\.com|platform\.twitter\.com)\/)/$script,third-party,xmlhttprequest,domain=promptfile.com
    /^https?\:\/\/(?!(ct1\.addthis\.com|s7\.addthis\.com|b\.scorecardresearch\.com|www\.google-analytics\.com|ajax\.googleapis\.com|static\.sockshare\.com)\/)/$script,third-party,xmlhttprequest,domain=sockshare.com
    /^https?\:\/\/(?!(feather\.aviary\.com|api\.aviary\.com|wd-edge\.sharethis\.com|w\.sharethis\.com|edge\.quantserve\.com|tags\.crwdcntrl\.net|static2\.pbsrc\.com|az412349\.vo\.msecnd\.net|printio-geo\.appspot\.com|www\.google-analytics\.com|loadus\.exelator\.com|b\.scorecardresearch\.com)\/)/$script,third-party,xmlhttprequest,domain=photobucket.com|~secure.photobucket.com

Could be replaced with these non-regex-based filters (longer, but more efficient to process):

    |http://$third-party,domain=firedrive.com|mediafire.com|promptfile.com|sockshare.com|photobucket.com|~secure.photobucket.com
    |https://$third-party,domain=firedrive.com|mediafire.com|promptfile.com|sockshare.com|photobucket.com|~secure.photobucket.com
    @@||ajax.cloudflare.com^$script,xmlhttprequest,domain=firedrive.com|mediafire.com
    @@||ajax.googleapis.com^$script,xmlhttprequest,domain=firedrive.com|mediafire.com|promptfile.com|sockshare.com
    @@||api.aviary.com^$script,xmlhttprequest,domain=photobucket.com
    @@||api-secure.solvemedia.com^$script,xmlhttprequest,domain=mediafire.com
    @@||api.solvemedia.com^$script,xmlhttprequest,domain=mediafire.com
    @@||az412349.vo.msecnd.net^$script,xmlhttprequest,domain=photobucket.com
    @@||b.scorecardresearch.com^$script,xmlhttprequest,domain=mediafire.com|photobucket.com|promptfile.com|sockshare.com
    @@||bp.yahooapis.com^$script,xmlhttprequest,domain=promptfile.com
    @@||connect.facebook.net^$script,xmlhttprequest,domain=firedrive.com|mediafire.com|promptfile.com
    @@||edge.quantserve.com^$script,xmlhttprequest,domain=photobucket.com
    @@||fbstatic-a.akamaihd.net^$script,xmlhttprequest,domain=firedrive.com|mediafire.com
    @@||feather.aviary.com^$script,xmlhttprequest,domain=photobucket.com
    @@||loadus.exelator.com^$script,xmlhttprequest,domain=photobucket.com
    @@||netdna.bootstrapcdn.com^$script,xmlhttprequest,domain=promptfile.com
    @@||platform.twitter.com^$script,xmlhttprequest,domain=promptfile.com
    @@||printio-geo.appspot.com^$script,xmlhttprequest,domain=photobucket.com
    @@||static2.pbsrc.com^$script,xmlhttprequest,domain=photobucket.com
    @@||static.sockshare.com^$script,xmlhttprequest,domain=sockshare.com
    @@||stats.g.doubleclick.net^$script,xmlhttprequest,domain=mediafire.com
    @@||tags.crwdcntrl.net^$script,xmlhttprequest,domain=photobucket.com
    @@||wd-edge.sharethis.com^$script,xmlhttprequest,domain=photobucket.com
    @@||w.sharethis.com^$script,xmlhttprequest,domain=photobucket.com
    @@||www.google.com^$script,xmlhttprequest,domain=mediafire.com
    @@||www.google-analytics.com^$script,xmlhttprequest,domain=firedrive.com|mediafire.com|photobucket.com|promptfile.com|sockshare.com

**Read carefully:** Not supporting regex-based filters has absolutely **nothing** to do with µBlock being more efficient than ABP. It's a myth. There is no truth to this. I insist on this here because I have seen this repeated a number of places.

The `$document` filter option is not supported, see [issue #405](https://github.com/gorhill/uBlock/issues/405). At time of writing, I see 10 such filters in _EasyList_.

**Read carefully:** Not supporting `$document` filter option has absolutely **nothing** to do with µBlock being more efficient than ABP. It's a principle thing: the purpose of the `$document` filter option is to disable a blocker on a specific site. I do not want µBlock to submit itself to 3rd-party filter lists for when it should completely disable it self.

#### "ABP has all the features µBlock has!"
No. µBlock currently offers you more:

- [Extends the filter syntax](https://github.com/gorhill/uBlock/wiki/Filter-syntax-extensions).
- [Local mirroring](https://github.com/gorhill/uBlock/wiki/Experimental-features#privacy-exposure-reduction-local-mirroring), a currently experimental but promising feature.
- [Dynamic filtering](https://github.com/gorhill/uBlock/wiki/Dynamic-filtering), the ability to point-and-click to filter on/off `script` and `iframe` tags, on a 1st- or 3rd-party basis. I consider this to be a [key feature](https://github.com/gorhill/uBlock/wiki/Dynamic-filtering---examples) of µBlock.
- Element picker is more modern.
- Let you select most common filter lists out of the box, without the need to import them first.
- Supports hosts files (hostnames are translated into the equivalent of `||www.example.com^`).
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