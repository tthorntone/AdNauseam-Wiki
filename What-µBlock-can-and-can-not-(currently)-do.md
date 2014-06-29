#### "µBlock does not support element hiding".

Yes it does. Try entering `twitter.com##body` in the _"Your filters"_ text area 
and visit twitter.com: the page will be blank.

What it doesn't support [yet](https://github.com/gorhill/uBlock/issues/4), 
is the UI counterpart to "element hiding", i.e. being able to click on an element 
to extract filters out of it.

#### "The memory usage isn't actually ABP's fault, _EasyList_ is like 40,000+ lines of rules that all have to be parsed by ABP".

µBlock also parse _EasyList_, _EasyPrivacy_, _Malware domains_ lists, 
and _Peter Lowes's Ad server_ list out of the box and yet uses less than half the 
memory of ABP.

#### "µBlock has all the features ABP has!"

No it doesn't. There are things ABP can do which µBlock can't at this time. I will 
consider all feature requests, but I will implement only those which do not jeopardize µBlock's
defining traits: lean, efficient and minimalist.

Filters with the `$popup` option are ignored. At time of writing, I see 558 such
filters in _EasyList_. Chromium comes with a built-in popup blocker, which can be enabled
in the settings.

Filters with the `$elemhide` option are ignored. At time of writing, I see 50 such
filters in _EasyList_. The purpose of these filters is to disable cosmetic filters on
specific site.

#### "µBlock has a smaller memory footprint than Ghostery or Disconnect."

No it doesn't. Last time I checked, µBlock has a larger memory footprint than both 
[Ghostery](https://www.ghostery.com) and [Disconnect](/disconnectme/disconnect). 
Regarding CPU footprint, I don't know, I didn't measure yet (maybe
I will). Keep in mind that µBlock, like ABP, Adguard, and some others allows users
to enter their own filters. There are also other differences, or similarities: µBlock, _Disconnect_
and ABP are licensed under [GPL](http://en.wikipedia.org/wiki/GNU_General_Public_License).