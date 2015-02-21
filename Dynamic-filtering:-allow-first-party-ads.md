[Back to "Dynamic-filtering"](https://github.com/gorhill/uBlock/wiki/Dynamic-filtering)

***

Someone asked me if it was possible to enable ads which originate only from the site itself, but without disabling uBlock for the site, so as to not allow 3rd-parties to inject their ads, trackers, analytics, etc.

This is actually possible using dynamic filtering: a simple locakl `allow` rule for the current site:

