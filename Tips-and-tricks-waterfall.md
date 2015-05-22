Short but very useful tips and tricks.

##### TechCrunch: [Firefox Will Soon Get Sponsored Suggested Tiles Based On Your Browsing History](http://techcrunch.com/2015/05/21/mozilla-will-soon-launch-sponsored-suggested-tiles-based-on-your-browsing-history/)

When creating a new tab and clicking a tile, here is what is reported for the behind-the-scene scope:

    09:36:36 xhr https://tiles.services.mozilla.com/v2/links/click
    09:36:34 xhr https://tiles.services.mozilla.com/v2/links/view

So here is a dynamic filtering rule to foil this new Firefox data-mining behavior:

    behind-the-scene tiles.services.mozilla.com * block

If you would rather not use dynamic filtering, the following custom static filter will also work:

    ||tiles.services.mozilla.com^$domain=behind-the-scene
