#### "µBlock is just a stripped-down version of HTTP Switchboard".

No. µBlock started off by extracting the pattern-filtering engines (net and cosmetic filters) from [HTTP Switchboard](https://github.com/gorhill/httpswitchboard#http-switchboard-for-chromium) ("HTTPSB"). These engines needed more work to bring them to maturity. Most of that work won't be ported back to HTTPSB. See ["The road ahead"](https://github.com/gorhill/httpswitchboard/issues/378) for details.

#### "µBlock does not support element hiding".

Yes it does. Try entering `twitter.com##body` in the _"Your filters"_ text area 
and visit twitter.com: the page will be blank.

#### "The memory usage isn't actually ABP's fault, _EasyList_ is like 40,000+ lines of rules that all have to be parsed by ABP".

µBlock also parse _EasyList_, _EasyPrivacy_, _Malware domains_ lists, 
and _Peter Lowes's Ad server_ list out of the box and yet uses less than half the 
memory of [Adblock Plus](https://adblockplus.org/) ("ABP"), which is itself much more efficient than 
[AdBlock](https://getadblock.com/) (at least this is what I have measured on Chromium-based browsers).

#### "µBlock has all the features ABP has!"

µBlock doesn't have a _"Block element"_ entry in the contextual menu (right-click). 

Regular expression-based filters are not supported. At time of writing I see three such filter in _EasyList_, and none in _EasyPrivacy_. So rather uncommon. I may support them if there is really a need, but only for those which will have the `domain` filter option set: otherwise it's just impossible to implement efficiently such filters, and µBlock won't encourage their use by supporting these. For all the instances I have seen, it is possible to translate them into more efficient non-regex-based filters.

Filters with the `$elemhide` option are ignored. At time of writing, I see 50 such filters in _EasyList_. The purpose of these filters is to disable cosmetic filters on specific sites.

#### "µBlock has a smaller memory footprint than Ghostery or Disconnect."

No it doesn't. Last time I checked, µBlock has a larger memory footprint than both 
[Ghostery](https://www.ghostery.com) and [Disconnect](/disconnectme/disconnect). That's for their own memory footprint. I didn't look into their contributions to the memory footprint added to each web page.

Regarding CPU footprint, I don't know, I didn't measure yet (maybe
I will). Keep in mind that µBlock, like ABP, Adguard, and some others allows users
to enter their own filters.

There are also other differences, or similarities: µBlock, _Disconnect_
and ABP are licensed under [GPL](http://en.wikipedia.org/wiki/GNU_General_Public_License). Also, there is [this](https://github.com/gorhill/uBlock/wiki/%C2%B5Block-and-others:-Blocking-ads,-trackers,-malwares).