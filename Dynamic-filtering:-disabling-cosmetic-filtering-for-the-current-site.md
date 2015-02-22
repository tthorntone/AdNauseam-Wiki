[Back to "Dynamic-filtering"](https://github.com/gorhill/uBlock/wiki/Dynamic-filtering)

***

Someone asked me if it was possible to disable cosmetic filtering for the current site, without disabling  µBlock, so as to keep the ability to block 3rd parties, to prevent them from injecting their ads, trackers, analytics, etc.

This is actually possible using dynamic filtering: a simple local `allow` rule (green) for the current site:

![Toggling on/off cosmetic filtering](https://raw.githubusercontent.com/gorhill/uBlock/master/doc/img/df-turn-off-cosmetic.gif)<br>
<sup>Only `twitter.com` is whitelisted, `google-analytics.com` is still blocked.</sup>

Using an `allow` rule for the current site will disable network **and** cosmetic filtering for the 1st-party domain.