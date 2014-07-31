##### Settings

Unlike HTTP Switchboard, µBlock can't foil cookie headers. I strongly suggest privacy-minded users to...

- Enable _"Block third-party cookies and site data"_ in _"Content settings"_ / _"Cookies"_.
    - It works very well: see "Outbound cookies" in [this benchmark results](https://github.com/gorhill/uBlock/wiki/%C2%B5Block-and-others:-Blocking-ads,-trackers,-malwares).
- Enable _"Click to play"_ in _"Content settings"_ / _"Plug-ins"_.

##### Command line switches

I personally use these command line switches (Chromium on Linux):

- `--disable-component-extensions-with-background-pages`
    - _"Disable default component extensions with background pages"_ ([ref](http://peter.sh/experiments/chromium-command-line-switches/#disable-component-extensions-with-background-pages))
    - I believe this prevent Hangout Services to be launched by the browser as a background process. I wasn't too happy to find out there was [such a process](https://code.google.com/p/chromium/codesearch#chromium/src/chrome/browser/resources/hangout_services/background.html) launched even though I do not use Google's _Hangout_.
    - With other Chromium-based browsers, maybe more stuff would be disabled, you decide whether this is good or bad.
- `--disable-background-networking`
    - _"Disable several subsystems which run network requests in the background"_ ([ref](http://peter.sh/experiments/chromium-command-line-switches/#disable-background-networking))
- [add more switch of interests whenever new ones are found]

##### Regarding EasyPrivacy

In case you were not aware, using _EasyPrivacy_ doesn't protect completely against Google Analytics. So if you were using Adblock Plus with _EasyPrivacy_ (as [recommended by the EFF](https://www.eff.org/deeplinks/2012/04/4-simple-changes-protect-your-privacy-online)), you might have thought you were protected against Google Analytics. [You are not](https://github.com/gorhill/uBlock/wiki/Tricks-and-tips#easy-way-to-find-out-what-other-blockers-do-not-block-what-they-should-block).

If you are using µBlock, no worry, it protects against Google Analytics out of the box -- via _"Peter Lowe's Ad server"_ list.

##### Twitter widget

I don't know why this one is not blocked by Fanboy Annoyance, as the list already blocks many other twitter widget-related stuff. So if you use above list, you may want to add the following to your filters:

`||platform.twitter.com/widgets.js$third-party`

##### Gravatar (et al)

Each time you visit a site which pull cute little avatar images aside (typically) a commenter's name, there is a corresponding request to [Gravatar](https://gravatar.com)'s web site, and the HTTP `referer` header contains the site you are visiting. The tracking potential is too much for me, so I block all these requests:

`||gravatar.com^$third-party`

I don't know if, and how much this breaks things. But for now I am happy to not have my browsing habits disclosed to gravatar.com. I can live without these cute thumbnails.

But this applies to any domain which is ubiquitous enough, `gravatar.com` is just one example among so many. To deal with this easily, I find HTTP Switchboard to be the best tool, as to blacklist a ubiquitous domain is simply a matter of point and click.