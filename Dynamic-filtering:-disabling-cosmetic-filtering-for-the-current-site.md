[Back to "Dynamic-filtering"](https://github.com/gorhill/uBlock/wiki/Dynamic-filtering)

***

Someone asked me if it was possible to disable cosmetic filtering for the current site, while keeping the ability to block 3rd-parties, so as to not allow these to inject their ads, trackers, analytics, etc.

This is actually possible using dynamic filtering: a simple local `allow` rule for the current site:

