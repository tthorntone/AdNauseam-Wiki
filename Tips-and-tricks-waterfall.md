Short but useful tips and tricks, randomly added.

#### Why using a blocker is **very important**

In response to this [ridiculously over-the-top pure propaganda](http://www.tomsguide.com/us/ad-blocking-is-stealing,news-20962.html) piece, whose purpose is to manipulate you into compliance to the one specific business model they chose for themselves. (Hint to _Tom's Guide_: nobody else but you is responsible for the failure of your chosen business model if it fails).

**Left:** without a blocker: 124 domains (note that I had Flash plug-in disabled, it would have been worse if it had been enabled -- I wasn't ready to go that far to make my point).

**Right:** default-deny with whitelisting of site's own domains (`bestofmedia.com`, `bestofmicro.com`): 3 domains.

The content of the picture below is not fabricated, it's really what was reported by uBlock.

[![c](https://cloud.githubusercontent.com/assets/585534/7784786/faefbef2-013f-11e5-95bc-afb5d79fd2c2.png)](https://cloud.githubusercontent.com/assets/585534/7784786/faefbef2-013f-11e5-95bc-afb5d79fd2c2.png)

As I often say, ads are only the small visible tip of the iceberg of the insidious privacy-invading data mining of people, without their _fully informed_ consent.

#### TechCrunch: [Firefox Will Soon Get Sponsored Suggested Tiles Based On Your Browsing History](http://techcrunch.com/2015/05/21/mozilla-will-soon-launch-sponsored-suggested-tiles-based-on-your-browsing-history/)

When creating a new tab and clicking a tile, here is what is reported for the behind-the-scene scope:

    09:36:36 xhr https://tiles.services.mozilla.com/v2/links/click
    09:36:34 xhr https://tiles.services.mozilla.com/v2/links/view

So here is a dynamic filtering rule to foil this new Firefox data-mining behavior:

    behind-the-scene tiles.services.mozilla.com * block

If you would rather not use dynamic filtering, the following custom static filter will also work:

    ||tiles.services.mozilla.com^$domain=behind-the-scene
