##### Intro

If you really care very much about your privacy (not being tracked, data mined, etc.), µBlock is a crutch (a good one though), even with _EasyPrivacy_ enabled (this is true for any "ad blocker"). If you want more than a good crutch, [HTTP Switchboard](https://github.com/gorhill/httpswitchboard#http-switchboard-for-chromium) is the way to go: it gives you full disclosure and full control of what web pages do.

##### Settings

Unlike HTTP Switchboard, µBlock can't foil cookie headers. I strongly suggest privacy-minded users to...

- Enable _"Block third-party cookies and site data"_ in _"Content settings"_ / _"Cookies"_.
    - It works very well: see "Outbound cookies" in [this benchmark results](https://github.com/gorhill/uBlock/wiki/%C2%B5Block-and-others:-Blocking-ads,-trackers,-malwares).
    - But this may break some sites. For instance, you won't be able to enter comments on Youtube.
    - Useful to know: the block also applies to local storages, not just cookies.
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

Another powerful command line switch is:

- `--host-rules="MAP *.google-analytics.com 0.0.0.0","MAP *.googleadservices.com 0.0.0.0","MAP *.doubleclick.net 0.0.0.0","MAP *.googletagservices.com 0.0.0.0"`
    - This switch maps those hostnames (or any other ones) to the IP address 0.0.0.0 ([ref](http://peter.sh/experiments/chromium-command-line-switches/#host-rules)) and hence blocks them effectively (even on the Chrome webstore where extensions like µBlock are disabled). 
    - _However, note that blocking those hostnames with that switch might break some websites. That's why blocking them with HTTP Switchboard is preferable since you can whitelist them as exceptions for those websites which won't work without them. Alternatively, you could use the `important` filter option mentioned below._

##### Regarding EasyPrivacy

In case you were not aware, using _EasyPrivacy_ doesn't protect completely against Google Analytics. So if you were using Adblock Plus with _EasyPrivacy_ (as [recommended by the EFF](https://www.eff.org/deeplinks/2012/04/4-simple-changes-protect-your-privacy-online)), you might have thought you were protected against Google Analytics. This is not necessarily the case.

If you are using µBlock, it protects you *more* against Google Analytics out of the box -- via _"Peter Lowe's Ad server"_ list. Yet, given that an exception filter may exist somewhere in one of the many lists, I can't guarantee the protection is 100%.

##### Overriding exception filters

However, in [µBlock 0.5.5.0](https://github.com/gorhill/uBlock/releases/tag/0.5.5.0) a new filter option `important` was introduced with the consequence that corresponding exception rules are ignored. Example: Adding

`||google-analytics.com^$important`

to "Your filters" blocks Google Analytics regardless of existing exception rules. You can restrict this rule to specific domains like

`||google-analytics.com^$important,domain=example1.com|example2.com`

or you could _exclude_ specific domains from this rule:

`||google-analytics.com^$important,domain=~example1.com|~example2.com`

Thus, this option is much more flexible than the above mentioned `--host-rules` command line switch.

##### Twitter widget

I don't know why this one is not blocked by Fanboy Annoyance, as the list already blocks many other twitter widget-related stuff. So if you use above list, you may want to add the following to your filters:

`||platform.twitter.com/widgets.js$third-party`

##### Gravatar (et al)

Each time you visit a site which pull cute little avatar images aside (typically) a commenter's name, there is a corresponding request to [Gravatar](https://gravatar.com)'s web site, and the HTTP `referer` header contains the site you are visiting. The tracking potential is too much for me, so I block all these requests:

`||gravatar.com^$third-party`

I don't know if, and how much this breaks things. But for now I am happy to not have my browsing habits disclosed to gravatar.com. I can live without these cute thumbnails.

But this applies to any domain which is ubiquitous enough, `gravatar.com` is just one example among so many. 

To deal with this easily, I find [HTTP Switchboard](https://github.com/gorhill/httpswitchboard) to be the best tool, as to blacklist a ubiquitous domain with 100% certainty is simply a matter of point and click.