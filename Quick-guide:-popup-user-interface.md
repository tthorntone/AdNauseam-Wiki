[Back to Wiki home](https://github.com/gorhill/uBlock/wiki)

***

- [The title bar](https://github.com/gorhill/uBlock/wiki/Quick-guide:-popup-user-interface#the-title-bar)
- [The large power button](https://github.com/gorhill/uBlock/wiki/Quick-guide:-popup-user-interface#the-large-power-button)
- [The number of requests blocked](https://github.com/gorhill/uBlock/wiki/Quick-guide:-popup-user-interface#the-number-of-requests-blocked)
- [The number of domains connected](https://github.com/gorhill/uBlock/wiki/Quick-guide:-popup-user-interface#the-number-of-domains-connected)
- [The site-based switches](https://github.com/gorhill/uBlock/wiki/Quick-guide:-popup-user-interface#the-site-based-switches)

***

This is uBlock's popup UI when you click on uBlock's icon in the toolbar:

![Popup UI](https://raw.githubusercontent.com/gorhill/uBlock/master/doc/img/popup-1.png)

***

#### The title bar

![Popup UI](https://raw.githubusercontent.com/gorhill/uBlock/master/doc/img/popup-1a.png)

Click the title bar of the popup to go to uBlock's dashboard.

***

#### The large power button

![Popup UI](https://raw.githubusercontent.com/gorhill/uBlock/master/doc/img/popup-1b.png)

Click the large power button to turn off uBlock **for the current site** (a.k.a. _whitelist_ the current site). This will be remembered the next time you visit the site.

Alternatively, you can also <kbd>Ctrl</kbd>-click to turn off uBlock only for the current page (<kbd>command ⌘</kbd>-click on Mac).

For more advanced whitelisting control, see ["How to whitelist a web site"](https://github.com/gorhill/uBlock/wiki/How-to-whitelist-a-web-site).

***

#### The number of requests blocked

![Popup UI](https://raw.githubusercontent.com/gorhill/uBlock/master/doc/img/popup-1c.png)

This shows the number of network requests which were blocked on the current page. Also, less useful, but people like this kind of thing, the number of network requests blocked since install.

Click the eye-dropper icon to enter [element picker mode](https://github.com/gorhill/uBlock/wiki/Element-picker), which allows to create a filter by interactively picking an element on a page, in order to have the element permanently removed from the page.

Click the eye icon to bring up the [network request logger](Quick-guide:-network-request-logger), which will open in a separate tab. This allows to inspect real-time network traffic on a given page.

***

#### The number of domains connected

![Popup UI](https://raw.githubusercontent.com/gorhill/uBlock/master/doc/img/popup-1d.png)

The number of distinct domains with which a network connection was established, out of all connections (established + blocked). The domains are derived using the official [Public Suffix List](https://publicsuffix.org/).

In general, it must be assumed that each distinct domain is managed by a distinct administrative authority. In practice, it is not uncommon to have a couple distinct domains which are under the same administrative authority (for example: `google.com`, `ajax.googleapis.com` and `gstatic.com`, or `wikipedia.org` and `wikimedia.org`).

That said, this statistic has to be seen this way: the more distinct domains your browser connects to, the larger the privacy exposure.

In a best-case scenario, the number of distinct domains to which a web page connects should be **only one**, i.e. that of the remote server from which the web page was fetched.

**The higher the number, the higher your are exposing yourself privacy-wise.**

There is a good correlation between _domains connected_ count and: undue page bloat, high privacy exposure, likelihood of being the target of data mining.

Example, a web page on <http://www.ibtimes.com/> (which could be read all fine in all cases by the way):

 uBlock's mode | turned off | default settings | [default-deny](https://github.com/gorhill/uBlock/wiki/Dynamic-filtering)
--- | --- | --- | ---
domains connected | ![](https://raw.githubusercontent.com/gorhill/uBlock/master/doc/img/popup-1e.png) | ![](https://raw.githubusercontent.com/gorhill/uBlock/master/doc/img/popup-1d.png) | ![](https://raw.githubusercontent.com/gorhill/uBlock/master/doc/img/popup-1f.png)
privacy exposure | very high | medium | very low
bloat | ridiculously high | medium | very low

And I had click-to-play enabled in all cases, i.e. it could have been worse (except for default-deny)...

***

#### The site-based switches

![Popup UI](https://raw.githubusercontent.com/gorhill/uBlock/master/doc/img/popup-1g.png)

The site-based switches allows to control uBlock's behavior on a per-site basis.

***

##### No popups

By default popups are allowed unless there is a filter to block them. When this setting is turned on, **all** popups will be unconditionally blocked for the current site, regardless of filters:

![Popup UI](https://raw.githubusercontent.com/gorhill/uBlock/master/doc/img/popup-1i.png)<br><sup>No popups for this site: [Try it](http://jessehakanen.net/adblockpluspopupaddon/test.html)</sup>

Blocking popups depends on whether the proper filters are present in the selected filter lists, so this feature is most useful for when a site create popups for which there are no filter to take care of them in 3rd-party filter lists.

***

##### No strict blocking

The second icon is to turn off strict blocking for the current site. By default strict blocking is on, this is the opposite of Adblock Plus.

As per ABP filter semantics, [web pages _themselves_ are **never** filtered](https://adblockplus.org/forum/viewtopic.php?t=18774#p85439), only secondary resources are subject to filtering.

So if you were to create a filter such as `||example.com^`, and then navigate to <https://example.com>, Adblock Plus would not prevent you from connecting and loading the web  page itself served at `https://example.com`, though it would filter all secondary resources pulled by that web page.

uBlock respected that semantic until version 0.9.3.0. With version 0.9.3.0, uBlock will subject web pages themselves to filtering. This means that using the same test case above, uBlock will block the web page served by <https://example.com> -- as opposed to ABP:

![Page was fully blocked](https://raw.githubusercontent.com/gorhill/uBlock/master/doc/img/page-block.png)

Why the change? Because [issue #1013](https://github.com/gorhill/uBlock/issues/1013) brought forth why it is desirable sometimes to block completely a web site, as opposed to what ABP-filtering semantic dictates.

In the end the chosen solution is to now have web page themselves subject to filtering just like all secondary resources.

In the figure above, a user will be given the choice to go back or proceed to the web page which was blocked. If the user chooses to proceed, web pages from the site will be temporarily allowed for a limited time (currently set at 60 seconds).

If the user disagree that a web page proper should be blocked (because of a false positive for example), then turning off _strict blocking_ for the site...

![Popup UI](https://raw.githubusercontent.com/gorhill/uBlock/master/doc/img/popup-1h.png)<br><sup>No strict blocking for this site.</sup>

... will prevent web pages proper for the site from being blocked by uBlock in the future: the filtering of the site will be done exactly as per ABP-filtering semantic, and just like with uBlock pre-0.9.3.0.

There are many benefits to strict blocking. For example, there is no good reason one should want to connect _at all_ to any of the sites present in any one of the malware domain lists. Strict blocking will prevent this from happening.

I expect the need to disable strict blocking to be rather uncommon.