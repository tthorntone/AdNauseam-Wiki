[Back to "Dynamic-filtering"](https://github.com/gorhill/uBlock/wiki/Dynamic-filtering)

***

Someone asked me if it was possible to disable cosmetic filtering for the current site, without disabling  µBlock, so as to keep the ability to block 3rd parties, to prevent them from injecting their ads, trackers, analytics, etc.

This is actually possible using dynamic filtering: a simple local `allow` rule for the current site:

