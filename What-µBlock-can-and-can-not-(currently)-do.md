#### "µBlock is just a stripped-down version of HTTP Switchboard".

No. µBlock started off by extracting the ABP engines (net and cosmetic filters) from HTTP Switchboard ("HTTPSB"). These engines needed more work to bring them to maturity. Most of that work has not been ported back to HTTPSB. Actually, I am questioning doing so, for the sake of code sanity, I consider removing ABP-filtering engine from HTTPSB, so that both extension complement each other, and with a narrower purpose, they can focus on doing what they do more perfectly.

Consider [this issue](/gorhill/httpswitchboard/issues/373) as a good example of how trying to do too many things lead to over-complicated software that I myself struggle to explain. Also, IMO a good way to sabotage a good piece of software is to turn it into a kitchen-sink tool.

The more I think about it, the more I am convinced this is the right thing to do. If you look closely at the [inner working of HTTPSB](/gorhill/httpswitchboard/wiki/Net-request-filtering:-overview), ABP-filtering is already a separate part.

#### "µBlock does not support element hiding".

Yes it does. Try entering `twitter.com##body` in the _"Your filters"_ text area 
and visit twitter.com: the page will be blank.

~~What it doesn't support [yet](https://github.com/gorhill/uBlock/issues/4), 
is the UI counterpart to "element hiding", i.e. being able to click on an element 
to extract filters out of it.~~ Never mind, it's now available in 0.2.0.0.

#### "The memory usage isn't actually ABP's fault, _EasyList_ is like 40,000+ lines of rules that all have to be parsed by ABP".

µBlock also parse _EasyList_, _EasyPrivacy_, _Malware domains_ lists, 
and _Peter Lowes's Ad server_ list out of the box and yet uses less than half the 
memory of [Adblock Plus](https://adblockplus.org/) ("ABP"), which is itself much more efficient than 
[Adblock](https://getadblock.com/) (at least this is what I have measured on Chromium-based browsers).

#### "µBlock has all the features ABP has!"

No it doesn't. There are things ABP can do which µBlock can't at this time. I will 
consider all feature requests, but I will implement only those which do not jeopardize µBlock's
defining traits: lean, efficient and minimalist.

~~Filters with the `$popup` option are ignored. At time of writing, I see 558 such
filters in _EasyList_. Chromium comes with a built-in popup blocker, which can be enabled
in the settings.~~ Supported in 0.2.1.0.

Filters with the `$elemhide` option are ignored. At time of writing, I see 50 such
filters in _EasyList_. The purpose of these filters is to disable cosmetic filters on
specific sites.

#### "µBlock has a smaller memory footprint than Ghostery or Disconnect."

No it doesn't. Last time I checked, µBlock has a larger memory footprint than both 
[Ghostery](https://www.ghostery.com) and [Disconnect](/disconnectme/disconnect). 
Regarding CPU footprint, I don't know, I didn't measure yet (maybe
I will). Keep in mind that µBlock, like ABP, Adguard, and some others allows users
to enter their own filters. There are also other differences, or similarities: µBlock, _Disconnect_
and ABP are licensed under [GPL](http://en.wikipedia.org/wiki/GNU_General_Public_License). Also, there is [this](https://github.com/gorhill/uBlock/wiki/%C2%B5Block-and-others:-Blocking-ads,-trackers,-malwares).