There are many lists out there which purpose is to enhance privacy protection. Many missing entries though. So here:

##### Settings

Unlike HTTP Switchboard, µBlock can't foil cookie headers. I strongly suggest privacy-minded users to...

- Enable _"Block third-party cookies and site data"_ in _"Content settings"_ / _"Cookies"_.
- Enable _"Click to play"_ in _"Content settings"_ / _"Plug-ins"_.

##### Regarding EasyPrivacy

In case you were not aware, using _EasyPrivacy_ doesn't protect against Google Analytics. So if you were using Adblock Plus with _EasyPrivacy_ (as [recommended by the EFF](https://www.eff.org/deeplinks/2012/04/4-simple-changes-protect-your-privacy-online)), you might have thought you were protected against Google Analytics. You are not.

If you are using µBlock, no worry, it protects against Google Analytics out of the box -- via _"Peter Lowe's Ad server"_ list.

##### Twitter widget

I don't know why this one is not blocked by Fanboy Annoyance, as the list already blocks many other twitter widget-related stuff. So if you use above list, you may want to add the following to your filters:

`||platform.twitter.com/widgets.js$third-party`

##### Gravatar

Each time you visit a site which pull cute little avatar images aside (typically) a commenter's name, there is a corresponding request to [Gravatar](https://gravatar.com)'s web site, and the HTTP `referer` header contains the site you are visiting. The tracking potential is too much for me, so I block all these requests:

`||gravatar.com^$third-party`

I don't know if, and how much this breaks things. But for now I am happy to not have my browsing habits disclosed to gravatar.com. I can live without these cute thumbnails.