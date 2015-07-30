[Back to Wiki home](https://github.com/gorhill/uBlock/wiki)

***

- [The title bar](https://github.com/gorhill/uBlock/wiki/Quick-guide:-popup-user-interface#the-title-bar)
- [The large power button](https://github.com/gorhill/uBlock/wiki/Quick-guide:-popup-user-interface#the-large-power-button)
- [The number of requests blocked](https://github.com/gorhill/uBlock/wiki/Quick-guide:-popup-user-interface#the-number-of-requests-blocked)
- [The number of domains connected](https://github.com/gorhill/uBlock/wiki/Quick-guide:-popup-user-interface#the-number-of-domains-connected)
- [The site-based switches](https://github.com/gorhill/uBlock/wiki/Quick-guide:-popup-user-interface#the-site-based-switches)
    - [No popups](#no-popups)
    - [No strict blocking](#no-strict-blocking)
    - [No cosmetic filtering](#no-cosmetic-filtering)
    - [No remote fonts](#no-remote-fonts)

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

This shows the number of network requests uBlock blocked on the current page. Also, less useful (but people like this kind of thing), the number of network requests uBlock blocked since you installed it. The percentage figure tells you how many requests were blocked out of all the requests made.

Click the _eye-dropper_ icon to enter [element picker mode](https://github.com/gorhill/uBlock/wiki/Element-picker), which allows you to create a filter by interactively picking an element on a page, thus permanently removing it from the page.

Click the _list_ icon to open the [network request logger](https://github.com/gorhill/uBlock/wiki/The-logger) in a separate tab. This allows you to inspect real-time network traffic within the browser.

***

#### The number of domains connected

![Popup UI](https://raw.githubusercontent.com/gorhill/uBlock/master/doc/img/popup-1d.png)

The number of **distinct** domains with which a network connection was established, out of all connections (established + blocked). The domains are derived using the official [Public Suffix List](https://publicsuffix.org/).

In general, it must be assumed that each distinct domain is managed by a distinct administrative authority. In practice, it is not uncommon to have a multiple distinct domains which are under the same administrative authority (example 1: `google.com`, `ajax.googleapis.com` and `gstatic.com`, example 2: `wikipedia.org` and `wikimedia.org`).

That said, this statistic may be seen this way: the more distinct domains your browser connects to, the greater the privacy exposure.

In a best-case scenario, the number of distinct domains to which a web page connects should be **only one**:  that of the remote server from which the web page was fetched.

**The higher the number, the higher you are exposing yourself privacy-wise.**

There is a good correlation between the _domains connected_ count and: unneeded page bloat, high privacy exposure, increased likelihood of being the target of data mining.

Example: the web page on <http://www.ibtimes.com/> (which can be read fine in all cases, by the way):

 uBlock's mode | turned off | default settings | [default-deny](https://github.com/gorhill/uBlock/wiki/Dynamic-filtering)
--- | --- | --- | ---
domains connected | ![](https://raw.githubusercontent.com/gorhill/uBlock/master/doc/img/popup-1e.png) | ![](https://raw.githubusercontent.com/gorhill/uBlock/master/doc/img/popup-1d.png) | ![](https://raw.githubusercontent.com/gorhill/uBlock/master/doc/img/popup-1f.png)
privacy exposure | very high | medium | very low
bloat | ridiculously high | medium | very low

And I had click-to-play enabled in all cases, so it could have been worse (except for default-deny)...

***

#### The site-based switches

![Popup UI](https://raw.githubusercontent.com/gorhill/uBlock/master/doc/img/popup-1g.png)

The site-based switches allows you to control uBlock's behavior on a per-site basis.

***

##### No popups

By default popups are allowed unless there is a filter to block them. When this setting is enabled, **all** popups will be unconditionally blocked for the current site, regardless of filters:

![Popup UI](https://raw.githubusercontent.com/gorhill/uBlock/master/doc/img/popup-1i.png)<br><sup>No popups for the current site: [Try it](http://jessehakanen.net/adblockpluspopupaddon/test.html)</sup>

Blocking popups depends on whether the proper filters are present in the selected filter lists, so this feature is most useful when a site creates popups for which there are no filters to take care of them in 3rd-party filter lists.

**Caveat for Chromium-based browsers:** Due to Chromium API limitations, it's not possible for uBlock to determine for sure whether a new tab being opened is that of a popup, or is the result of a legitimate click on a link by the user. So if the no-popups switch is in use, you won't be able to open a link in a new tab through the context menu.

***

##### No strict blocking

The second icon is to turn off strict blocking for the current site. By default, strict blocking is enabled in uBlock (this is the opposite of Adblock Plus).

Adblock Plus only blocks secondary resources (see [web pages _themselves_ are **never** filtered](https://adblockplus.org/forum/viewtopic.php?t=18774#p85439)).

So if you were to create a filter such as `||example.com^`, and then navigate to <https://example.com>, Adblock Plus would not prevent you from connecting and loading the web page itself served at `https://example.com`, though all secondary resources pulled by that web page would be subject to filtering.

uBlock respected that semantic until version 0.9.3.0. With version 0.9.3.0, uBlock will subject web pages themselves to filtering. This means that using the same test case above, **uBlock will block the web page** served by <https://example.com> (unlike Adblock Plus):

![Page was fully blocked](https://cloud.githubusercontent.com/assets/585534/8160013/14466ca0-133a-11e5-8d3c-28169288f35a.png)

Why the change? Because [issue #1013](https://github.com/chrisaljoudi/uBlock/issues/1013) brought forth why it is desirable sometimes to completely block a web site, as opposed to what the ABP-filtering semantic dictates.

In the end, the chosen solution is to now have web page themselves subject to filtering, just like all secondary resources.

In the figure above, the user will be given the choice to go back by closing the window or proceed to the web page by disabling strict blocking by selecting either:

- Temporarily - The site will be temporarily allowed for a limited time (currently set at 60 seconds).
- Permanently - The site will be permanently allowed.

If the user disagrees that a web page proper should be blocked (because of a false positive for example), then they can turn off _strict blocking_ for that site:

![Popup UI](https://raw.githubusercontent.com/gorhill/uBlock/master/doc/img/popup-1h.png)<br><sup>No strict blocking for the current site.</sup>

This will prevent the web page proper for the site from being blocked by uBlock in the future: the filtering of the site will be done exactly as per ABP-filtering semantic, and just like with uBlock pre-0.9.3.0.

There are many benefits to strict blocking. For example, there is no good reason one should want to connect _at all_ to any of the sites present in any one of the malware domain lists. Strict blocking will prevent this from happening.

I expect the need to disable strict blocking to be rather uncommon.

**Important note:** Keep in mind that when the above warning occurs, it doesn't necessarily mean the site is harmful, it just means that there is a matching filter in the selected filter lists. You decide whether the site is safe, and whether disabling strict blocking permanently for the site is appropriate.

***

##### No cosmetic filtering

You can easily toggle on/off cosmetic filtering for a given site:

![Popup UI](https://raw.githubusercontent.com/gorhill/uBlock/master/doc/img/popup-1j.png)<br><sup>No cosmetic filtering for the current site.</sup>

When present, the badge number indicates the number of elements hidden on the page by uBlock as a result of cosmetic filtering. If you disable cosmetic filtering while there are hidden elements on the page, these elements will become visible/hidden as you toggle off/on cosmetic filtering.

Cosmetic filtering is always enabled by default.

**Tip:** It is often suggested adding a custom static filter such as `@@||example.com^$elemhide` to prevent "adblock" detection by specific sites ([example](https://adblockplus.org/forum/viewtopic.php?f=2&t=30763#p124225)). You can accomplish the same goal more simply by just toggling off cosmetic filtering using this switch while on the problematic site.

***

##### No remote fonts

You can prevent web fonts from being downloaded for the current site:

![Popup UI](https://raw.githubusercontent.com/gorhill/uBlock/master/doc/img/popup-1k.png)<br><sup>No remote fonts for the current site.</sup>

Because of security and privacy concerns, many prefer to block all web fonts by default. You can do this by adding the following rule directly in the _"My rules"_ pane in the dashboard:

    no-remote-fonts: * true

This will block all web fonts everywhere by default, and in this case you can toggle off the switch to allow web fonts on a per-site basis.

**Caveat for Chromium-based browsers:** Chromium's webRequest API [does not specifically report requests of type `font`](https://developer.chrome.com/extensions/webRequest#type-ResourceType), fonts are reported as type `other`. Whether a request is for a font resource is inferred by uBlock using the "extension" of the path part of a URL. However a URL can be anything really, regardless of request type, so for Chromium-based browsers, uBlock **may** have to block a font **after** the request is made, when the response headers are received from the remote server -- as the response headers allow to identify for sure the type of a resource.